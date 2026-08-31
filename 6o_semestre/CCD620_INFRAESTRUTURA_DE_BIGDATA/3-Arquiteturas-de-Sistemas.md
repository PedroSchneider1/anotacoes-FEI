# Aula 3 - Arquitetura de Sistemas

> Escolha uma empresa/órgão/projeto que tenha algum serviço relacionado a big data e estude a arquitetura usada por esta empresa. Tente responder perguntas como:

**Empresa escolhida:** Discord

**Tema:** Como o Discord armazena trilhões de mensagens

**Fonte:** [Como o Discord armazena trilhões de mensagens](https://discord.com/blog/how-discord-stores-trillions-of-messages)

## Qual o problema tentou resolver?

Basicamente o Discord migrou do **mongoDB** pro **Cassandra** em 2017, mas o Cassandra apresentou alguns problemas de **escalabilidade** quando tiveram que escalar pra armazenar **trilhões de mensagens**.

Acontece que o cassandra não escalou como esperado, e por conta disso eles tinham que fazer diversas operações não previstas. Um dos pontos levantados pelo autor do post diz que a leitura era muito mais custosa no cassandra,formando algumas **"partições quentes"** já que tinha que acessar as **memtables** para encontrar as mensagens.

Além disso, o autor menciona um problema com a **JVM** (presente no cassandra), já que as vezes o **garbage collector** falhava, forçando os desenvolvedores a droppar o nó em questão pra conseguir desalocar os objetos em memória. Além disso, as pausas do **garbage collector** aumentavam a **latência entre os nós**.

## Qual a taxa de transferência dos dados esperado?

Com a resolução final do problema a **latência** passou de **40-125ms no Cassandra para 15ms no Scylla**.

## Quais serviços/produtos ela escolheu para usar?

A ferramenta escolhida (ou melhor,o **banco de dados** escolhido) foi o **ScyllaDB**. Ele possui um funcionamento semelhante ao **Cassandra** e foi escrito em **C++**,o que já é uma vantagem em relação ao **Garbage Collector**.

Um dos problemas porém encontrados no Scylla foram as **consultas reversas**. Uma consulta reversa pode ocorrer (como no exemplo do autor) quando era realizada uma tentativa de verificar o banco de dados na ordem oposta da classificação de uma tabela, como quando se digitaliza mensagens em ordem crescente. Contudo, isso rapidamente foi resolvido pela equipe do próprio **ScyllaDB**.

## Como isto resolveu o problema? Como foi implementado?

A solução do problema não se baseia somente na troca de banco, pois o fenômeno das **"partições quentes"** poderia acontecer novamente com o Scylla devido ao volume de dados e consultas.Tendo isso em mente, os programadores idealizaram um novo serviço, chamado de **serviço de dados**.

A ideia desse serviço de dados era ficar entre o **monolito** e os **clusters do banco** (numa analogia porca feita por mim, poderíamos imaginar como um **load balancer pra dados**) e é nesse contexto que surge a segunda ferramenta para resolver o problema: **Rust**.

Esse serviço não contém nenhuma **regra de negócio** e se utilizam de **gRPC** pra transmitir os dados. A grande sacada do serviço de dados é que caso vários usuários solicitem a mesma linha ao mesmo tempo, ele sõ consulta o banco uma única vez (diferente do modelo anterior que gerariam várias consultas). O primeiro usuário a solicitar o dado gera uma **task**, e os usuários subsequentes que quiserem esses dados vão primeiro verificar se alguém já o solicitou (basicamente um **publisher-subscriber gigante**).

No discord nós temos o **@everyone**, que marca todos daquele servidor naquela mensagem.Isso antigamente poderia resultar em uma **partição quente**, já que todos os usuários iriam solicitar o dado uma vez.

Além disso eles usaram **hash** pra permitir uma aglutinação mais eficaz dessas solicitações, reduzindo a **carga no banco**.

Ainda tiveram alguns problemas com a **migração**, já que devido ao volume de dados era extremamente complexa e na estimativa inicial levaria cerca de **3 meses**. Por conta disso, a equipe achou melhor reescrever uma ferramenta de migração em **Rust** (novamente salvando o dia), o que diminuiu o tempo para **9 dias**

## Quais problemas a ainda estão em abertos? Como eles poderiam ser resolvidos?

Não aparentam existir problemas relevantes em aberto após a implementação da solução apresentada. A combinação do **ScyllaDB**, do **serviço de dados** e das otimizações realizadas em **Rust** resolveu os principais problemas de escalabilidade, latência e sobrecarga que existiam anteriormente. Dessa forma, a arquitetura implementada conseguiu atender às necessidades do Discord de armazenar e consultar **trilhões de mensagens** de forma mais eficiente.
