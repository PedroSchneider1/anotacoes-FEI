# Aula 4 - Arquitetura Lambda


> O objetivo no final da aula é saber explicar o propósito da arquitetura lambda, diferenciar batch layer, speed layer e serving layer, além de decidir quando lambda é adequado ou não.


### Por que usar Lambda?

A ideia é tentar resolver problemas que precisam de resposta rápida e visão histórica confiável. Teoricamente se processarmos somente batch teremos atraso, em contra partida utilizar somente stream pode dificultar recomputação completa.

**Relembrando:** Batch processa em lote, serve pra coisas que não precisam de uma resposta imediata e que rodam em um horário pré-determinado. Até processar, acumulamos os dados.

Stream: Lida com tudo em tempo real, processando à medida que chega. Podemos relembrar do exemplo da fraude no banco digital, não adianta nada me avisarem que teve uma transação suspeita na minha conta 2 dias depois. Diferentemente do batch, o stream precisa que os dados sejam tratados assim que entram no sistema.

Nesse contexto surge a arquitetura lambda, que promete combinar os dois pra equilibrar os prós e contras.

### Definição

> Na arquitetura lambda temos um padrão de três camadas:

**Batch layer:** Exatidão histórica e recomputação.
**Speed layer:** Baixa latência para dados recentes.
**Serving layer:** entrega de consultas para consumo.


Podemos resumir a arquitetura lambda com a seguinte visão geral:

> fonte de dados -> ingestão de eventos -> (batch + speed) -> serving -> consumo


O mesmo evento vai alimentar os dois aminhos (histórico e tempo real) e a resposta final combina os dois resultados.


### Batch layer:

Vai armazenar o histórico completo (dados imutáveis quando possível), reprocessa grandes volumes com as regras de negócio atualizadas e produz visões consistentes e consolidadas.

**Prós:** 
- Recupera exatidão mesmo após falhas no processamento em tempo real.
- Forte pra auditoria, compliance e métricas históricas.
- Alta capacidade de processamento

**Contras:**  
- Maior latência (minutos, horas ou dias).


### Speed layer:

Diferentemente da Batch, processa os eventos assim que chegam, atualiza ndicadores de **curto prazo** com baixa latência e compensa o atraso que o batch naturalmente possui.

**Benefício Principal:** Permite decisões operacionais imediatas.

**Prós:**
- Latência baixa (na casa dos segundos/milisegundos).
- Normalmente processa janela recente dos dados.

**Contras:**
- Maior sensibilidade a falhas e duplicidade
- Normalmente processa janela recente dos dados (desvantagem?)


#### Serving layer:

Vai expor os dados para API's, dashboards e aplicações.
Unifica saída batch + speed pra essa consulta e define contratos de acesso, SLA e governança de consumo.

**Objetivo:** Entregar a melhor resposta possível no tempo necessário.


### Como funciona?


Ai que vem a malandragem, basicamente vamos ter um histórico consolidado (que veio do batch) e dados mais recentes (vindos da speed) complementando. Aplicamos uma regra de merge por tempo/chave (responsa da serving layer) e como resultado vamos ter uma visão "quase"   



