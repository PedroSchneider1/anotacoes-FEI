# Parte A:
#Link: https://www.youtube.com/watch?v=xcg1o0ycNc0

O que é design (projeto)?
	é um processo com três atividades básicas:

- **Análise da situação atual**: estudar e interpretar a situação atual;
- **Síntese de uma intervenção**: planejar e executar uma intervenção na situação atual;
- **Avaliação da nova situação**: verificar o efeito da intervenção comparando a situação analisada anteriormente com a nova situação, atingida após a intervenção.

<img src="../../../Screenshots/projetoIHC-A-im1.png"/ width="80%" height="80%" />
### Perspectivas de projeto:
São formas de interpretar a atividade de projeto (design)
- **Racionalismo técnico**: Problemas e soluções conhecidos, métodos de solução bem definidos a priori, designer enquadra uma situação num tipo geral de problema cuja forma de solução seja conhecida
- **Reflexão em ação**: Problemas e soluções únicos, métodos e ferramentas para auxiliar o aprendizado do designer sobre o problema e solução únicos, designer busca aprender sobre o problema em questão e a solução sendo concebida.
### Processos de Projeto de IHC:
- **Ciclo de vida simples**
	- Identificar necessidades e definir requisitos -> (re)design -> construir uma versão interativa -> avaliar -> produto final

- **Ciclo de vida em estrela**
	- Avaliação -> análise de tarefas, usuários e funções, especificação de requisitos, projeto conceitual e especificação do design, prototipação, implementação

- **Engenharia de Usabilidade de Nielsen**
	 - Conheça seu usuário -> Realize uma análise competitiva -> Defina as metas de Usabilidade -> Faça designs paralelos -> Adota o design participativo -> Faça o design coordenado da interface como um todo -> Aplique diretrizes e análise heurística -> Faça protótipos -> Realize testes empíricos -> Pratique design iterativo

- **Engenharia de Usabilidade de Mayhew**
	 - Ciclo da Engenharia de Usabilidade: perfil do usuário -> análise de tarefas -> características da plataforma -> princípios gerais de projeto - metas de usabilidade -> guia de estilo
	<img src="../../../Screenshots/mayhewIHC.png"/ width="80%" height="80%" />

- **Design Contextual**
- **Design Baseado em Cenários**
- **Design Dirigido por Objetivos**
- **Design Centrado na Comunicação**

# Parte B:
#Link: https://www.youtube.com/watch?v=PgCMewnIDt8

Análise de requisitos (engenharia de Usabilidade de Mayhew)

Perfil do usuário: Personas e pesquisas
Análise de Tarefas: HTA, GOMS, CTT e etc
### Características da Plataforma:

Análise das capacidades e restrições da plataforma: Devem ser examinadas as possibilidades e restrições em termos de equipamentos, os's, ambientes de janelas, recursos de rede etc.

Criar uma tabela com coluna de capacidades e de restrições. Descreva e Justifique.

### Princípios gerais de projeto:

Análise de princípios gerais para o projeto: Pesquisa e catalogação do conhecimento ergonômico disponível para a concepção da interface do tipo de contexto de uso(usuário, tarefa, equipamento e ambiente) no qual o sistema está inserido.
Documente com links documentos importantes para seu contexto de aplicação e normas para boa interface.

### Metas de Usabilidade:

Especificação dos objetivos da usabilidade: 
Contexto de uso:  Usuário, tarefa, condições ambientais (software, equipamento, ambiente físico e organizacional).

Exigências para a usabilidade:
Exigências qualitativas para a interface - Requisitos em termos de funções e de características de interface que devem ser implementadas de modo a melhor satisfazer o tipo de usuário, tarefa e plataforma especificados.

Exigências quantitativas para a usabilidade - Nível de usabilidade esperado para o sistema. Essa especificação é feita nos termos de valores mínimos admissíveis para os fatores básicos de usabilidade: eficácia, eficiência e satisfação do usuário principalmente.
### Guia de estilo:

Registra todas as decisões tomadas nesta e nas demais fases do desenvolvimento e devem ser registradas em um documento oficial.

# Parte C:
#Link: https://www.youtube.com/watch?v=mnAv1lOhodU
### Nível 1:
- Projeto essencial
- Reengenharia do Trabalho

Modelagem de alternativas de projeto, nas quais os projetistas especificam as telas e componentes essenciais da interface, bem como a navegação entre elas.
É concretizado de forma de Maquete (lápis e papel) Desenhos abstratos de janelas ou caixas de diálogo contendo apenas os componentes essenciais para a tarefa.
O importante nesta etapa é que as representações não sejam detalhadas, o que evita que se gaste um tempo importante do projeto em definições precoces.

- Simulação dupla: os representantes de usuários simulam a realização de tarefas fundamentais do sistema (imaginando que as maquetes sejam o próprio sistema). Já os projetistas simulam o comportamento do sistema, tipicamente apresentando novas telas em papel em resposta a uma ação do usuário.

### Nível 2:
- Padrões de telas e Diálogos

É uma adaptação do guia de estilo (guide line) do ambiente de janelas (Windows, Mac, Swing Java...) no qual o sistema será executado. A adaptação deve ser feita com base nos resultados da etapa de análise de requisitos (principalmente as definições sobre o contexto de uso e as exigências para a usabilidade) e das definições do modelo conceitual da interface.

- Padrões de Telas
- Protótipo de baixa fidelidade

Será capaz de dialogar com o usuário, mas não estará ligado a uma base de dados.

- Testes

Simulações mais realistas do uso do sistema. Torna-se possível nesta etapa realizar testes de usabilidade mais detalhados, produzindo medidas objetivas sobre a eficácia, a facilidade de aprendizado e a taxa de erros do usuário na tarefa.

### Nível 3:
- Projeto Detalhado

O projetista integra ao projeto os  aspectos não essenciais até então desconsiderados, tanto no que se refere ao modelo conceitual da interface quanto aos padrões de telas.

Simulações ainda mais próximas da realidade.

A. Projeto essencial;
B. Padrões de telas e diálogo;
C. Projeto detalhado.

Devem ser repetidos nesta sequencia para cada grupo de funcionalidades essenciais da interface do sistema com o seu usuário.
### Instalação

Feedback do usuário: Depois de algum tempo de uso o usuário já está acostumado com o sistema e pode ser considerado especialista.
Detectar e eliminar problemas de ultima hora e preparar um novo release do produto
### Design Contextual:

- investigação minuciosa do contexto de uso;
- investigação contextual
- modelagem do trabalho (fluxo do trabalho, baseado nos contextos do produto criado)
- consolidação da modelagem do trabalho
- reprojeto do trabalho
- projeto do ambiente do usuário
- prototipação 
- testes com usuários

Design Dirigido por Objetivos, Design centrado na Comunicação
### Integração de IHC com Engenharia de Software

As principais abordagens de integração são:

- Definição de características de um processo de desenvolvimento que se preocupa com a qualidade de uso
- Definição de processos de IHC paralelos que devem ser incorporados aos processos propostos pela ES;
- Indicação de pontos em processos propostos pela ES em que atividades e métodos de IHC podem ser inseridos

