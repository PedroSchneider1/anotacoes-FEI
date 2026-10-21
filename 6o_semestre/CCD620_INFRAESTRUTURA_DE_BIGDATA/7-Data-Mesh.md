# Data Mesh


### Objetivos:


• Explicar o que é data mesh e por que surgiu;

• Descrever os quatro princípios (dominios, dados como produto, plataforma, self-service e governançca federada);

• Mapear domínios de um banco digital em produtos de dados;

• Discutir tradeoffs entre autonomia de times e governança central e discutir quando Data Mesh é adequado ou não para um contexto de negócios.




### Contexto -> A Plataforma Centralizada:

Basicamente no modelo tradicional tem um time central de dados que atende a empresa toda, logo eles tem que fazer desde ingestão, modelagem, dashboards e extrações. Isso até funciona quando a empresa é pequena e tem poucos domínios, mas conforme a empresa cresce esse time central vira um gargalo (muitas demandas), o conhecimento de negócio fica longe de quem processa os dados e pipelines genéricos perdem a semântica de cada domínio.

### Problema que o Data Mesh resolve

Basicamente não precisa escalar o time de dados de acordo com a complexidade do negócio, já que quem conhece o dado (domínio) não é o dono do dado. 
A falta de Ownership gera baixa qualidade e pouca confiança. Mudanças em sistemas de **origem** quebram consumidores sem aviso e as cópias manuais (planilhas, extrações) se multiplicam sem controle.

### Definição

Data Mesh é classificado como uma abordagem **sociotécnica** de arquitetura de dados, que distribui a responsabilidade pelos dados aos domínios de negócio.


> Ownership por domínio + Dados como produto + Plataforma self-service + governançca federada


**Obs:** Não é uma ferramenta, é organização + processos + plataforma

O dado deixa de ser subproduto e passa a ser produto com dono.


### Os quatro princípios


- **01. Ownership orientado a domínio**
- **02. Dados como produto**
- **03. Plataforma de self-service**
- **04. Governança computacional federada**

 
### Princípio 1 - Ownership por domínio

Cada domínio de negócio é dono dos dados que gera, então o time do domínio publica, mantem e tem que responder por esses dados
Quem entende o negócio define a semântica e a qualidade

> Benefício principal: qualidade e contexto na origem, não corrigidos depois no ETL central


### Princípio 2 - Dados como produto

Dados tratados como produto tem consumidores, SLA, documentação e versionamento

Um bom produto de dados é:

- **01. Descobrível**
- **02. Confiável (SLA)**
- **03. Autodescritivo**
- **04. Interoperável e seguro**

> Benefício principal: Consumo sem depender de extrações manuais ou do time central (eu rodando query pro rabelo).

### Princípio 3 - Plataforma self-service

Time de plataforma (eu) oferece ferramentas prontas:

Ingestão, storage, processamento, catálogo e observabilidade (fixee-relatórios)

Os domínios constroem e operam os seus produtos, sem depender do time central e a plataforma esconde a complexidade da infraestrutura


> Benefício principal: escala times sem gargalo central


### Princípio 4 - Governança Federada

Pra funcionar precisamos de regras globais (padrões, segurança, privacidade e etc) definidas por um fórum federado com representantes dos domínios

Execução automatizada pela plataforma (policies as code)

Domínios têm autonomia dentro das regras comuns

> Benefício principal: equilíbrio entre autonomia dos times e conformidade da empresa


### Visão geral do fluxo

**Sequência:**

> Sistemas transacionais -> Produtos de dados por domínio -> Catálogo/Plataforma -> Consumidores (BI, ML, APIs, regulação)


### Usando o banco de exemplo

Banco digital com os serviços usados hoje:

Conta digital e pix, Cartões, Crédito, Investimentos e Open Finance, Antifraude, Atendimento e etc

> Regra do mesh: cada serviço vira um domínio dono do seus dados.


### Domínio: Pagamentos e Pix

Sistemas: Core banking, SPI/Pix, gestão de contas.

Produtos de dados publicados: 

**pix-Liquidação** (eventos de liquidação, janela de 15 min)
**saldos_diarios** (posição consolidada por conta)
**limites_transacionais**

 - Consumidores: Risco, financeiro e tesouraria.



> Mensagem chave: No Mesh todo mundo é produtor e consumidor ao mesmo tempo.





