# GOMS:

-  Objetivos (goals):  Representam o que o usuário quer realizar utilizando o sistema

- Operadores: primitivas internas(cognitivas) ou externas (ações concretas que o sistema  permite que os usuários façam, tal como um comando e seus parâmetros digitados num teclado; a seleção de menus; o clique de um botão)

- Métodos: Sequência bem conhecidas de subobjetivos e operadores que permitem atingir um objetivo maior

- Regras de Seleção: Permitem decidir qual método utilizar numa determinada situação

## Exemplo de GOMS:

```
GOAL 0: descobrir direção de tráfego de uma rua
	GOAL 1: encontrar a rua
		METHOD 1.A: zoom até o nível de ruas
			(SEL.RULE: a região em que se situa a rua está visível no mapa e o usuário conhece o local).
			OP 1.A.A: fazer tal coisa
			OP 1.A.B: fazer tal coisa
			OP 1.A.C: VERIFICAR tal coisa
		METHOD 1.B: fazer busca pelo nome da rua
			(SEL.RULE: o usuário não conhece o local ou o mapa visivel está longe de lá).
			OP 1.B.A: fazer tal coisa
			OP 1.B.B: fazer tal coisa
			OP 1.B.C: VERIFICAR tal coisa
	GOAL 2: identificar a direçãodo tráfego na rua
			
```


Os operadores primitivos internos envolvem o cognitivo, ou seja, verificar algo (algo que se faça na cabeça do usuário), e os externos são tudo que interagem pela interface do sistema sem passar pelo cognitivo.


## Modelo GOMS-KLM

Utiliza o tempo das ações para  analisar diferentes propostas de interface.

	Clicar em x coisa - 0,4 segundos
	Identificar o ícone x - 1,0 segundos
	Clicar em "salvar" - 0,5 segundos
	Nomear o arquivo - 2,0 segundos

Vs

	Utilizar o atalho CTRL + S- 0,2 segundos
	Nomear o arquivo - 2,0 segundos

Com isso podemos perceber uma diferença entre os 3,9 segundos da primeira proposta e os 2,2 segundos da segunda proposta, o que nos ajuda identificar diferentes tipos de interface e tomar decisões conforme as necessidades do sistema.

# CTT:

Auxilia a avaliação e o design

Existem 4 tipos de tarefas:

- **Tarefas do usuário**: realizadas fora do sistema
- **Tarefas do sistema**: em que o sistema realiza um processamento sem interagir com o usuário
- **Tarefas Interativas**: em que ocorrem os diálogos usuário-sistema
- **Tarefas Abstratas**: que não são tarefas em si, mas sim uma representação de uma composição de tarefas que auxilie a decomposição.

A diferença do CTT para os outros é que ele é o único que nos permite mapear a experiência do usuário e briefing, pois este método permite documentar o que motivou o usuário antes de utilizar o sistema (lembra do CrossMedia), diferentemente dos outros métodos de análise de tarefas que se baseiam somente na interação com o sistema.

## Relação entre tarefas no CTT:

- **Ativação**: T1>>T2 significa que a T2 só pode começar quando a T1 acabar

- **Ativação com passagem de informação**: T1\[]>>T2 basicamente a mesma coisa só que T2 recebe informação produzida por T1 (return)

- **Escolha**(tarefas alternativas): T1\[]T2 basicamente só roda uma, porém qual delas vai primeiro não importa

- **Tarefas concorrentes**: T1|||T2 as tarefas podem ser realizadas em qualquer ordem ou ao mesmo tempo

- **Tarefas concorrentes comunicantes**: T1|\[]|T2 além de poderem ser em qualquer ordem ou ao mesmo tempo, ainda trocam informações entre si.

- **Tarefas independentes**: T1 |=|T2 especifica que as tarefas podem ser realizadas em qualquer ordem, mas quando uma termina a outra só começa quando a primeira terminar.

- **Desativação**: T1\[>T2 especifica que T1 é completamente interrompida por T2

- **Suspensão/Retomada**: T1| > T2 especifica que T1 pode ser interrompida por T2 e é retomada no ponto em que parou assim que T2 terminar

<img src="../../../Screenshots/relaçãoCTT.png"/ width="80%" height="80%" />

### Exemplo
<img src="../../../Screenshots/exCTT.png"/ width="80%" height="80%" />