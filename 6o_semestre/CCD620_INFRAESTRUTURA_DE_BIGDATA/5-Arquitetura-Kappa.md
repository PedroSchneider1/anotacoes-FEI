# Arquitetura Kappa


### Hoje eu tenho que sair da aula sabendo:


• explicar o propósito da arquitetura Kappa em plataformas de dados;
• diferenciar claramente event log, processamento contínuo e serving layer;
• discutir trade-offs entre latência, retenção de eventos e consistência;
• decidir quando Kappa é adequada (ou não) para um contexto de negócio.



### Problemas que a arquitetura Kappa resolve:

Basicamente ele serve para problemas que precisam de resposta rápida e capacidade de reprocessamento ao mesmo tempo. Na semana passada vimos a lambda que separava speed de batch epra isso tinha que duplicar as pipelines, já no Kappa aparentemente não precisamos duplicar.
Isso vai facilitar pra quando estivermos desenvolvendo em algum cenário event-driven (orientado a eventos) e justamente é isso que a arquitetura Kappa utiliza pra equilibrar os requisitos do problema, centraliza o fluxo em eventos.


### Definição

A **Kappa** tem três blocos funcionais:

> event_log + processamento_contínuo + serving_layer

**Event Log:** Histórico sequencial de eventos como a nossa fonte da verdade

**Processamento Contínuo:** Transformação em tempo real com estados/janelas

**Serving Layer:** Entrega de consultas para consumo

### Visão Geral do Fluxo

> Fonte de dados -> Ingestão de eventos -> event_log -> processamento contínuo -> serving -> consumo

O mesmo evento vai alimentar o processamento em tempo real. Os reprocessamentos ocorrem por replay do log, sem trilha de batch paralela.

### Event log - Características

Alta capacidade de ingestão e leitura, retenção configurável por tempo ou tamanho, dependência de bom particionamento por chave de negócio (exemplo da secretaria, utiliza a hora ao invés do RA pra armazenar os eventos), forte necessidade de governança de **schema** e versionamento (pra não mandar qualquer formato e quebrar tudo).

### Processamento contínuo - Papel

Temos que processar os eventos assim que chegarem e atualizar os indicadores e estados com **baixa latência**. Isso substitui a necessidade de speed + batch separados.

Benefício principal: simplifica a topologia para decisões operacionais imediatas.

### Processamento contínuo - Características

Latência baixa (na casa dos segundos ou milissegundos), **PRECISAMOS** de mecanismos de idempotência e controle de estado, necessitamos de checkpoints e recuperação consistente e precisamos operar com semântica de entrega bem definida.

### Serving Layer - Papel

Serve pra expor os dados pra API's, dashboards e aplicações, entrega visões materializadas provenientes do processamento contínuo, define contratos de acesso, SLA e governança de consumo.

**Objetivo:** Entregar a melhor resposta possível no tempo necessário.



### Como a visão unificada funciona

Estratégia comum: o estado atual é derivado continuamente do fluxo de eventos, temos visões materializadas que são atualizadas em tempo real e quando a regra muda, o replay reconstrói a visão consolidada.

Como resultado, temos uma visão **quase** em tempo real com histórico reconstruível via eventos.

### Exemplo de uso

Monitorar transações e comportamento de usuários.

- alerta imediatos de risco (stream)
- recalcular métricas com nova regra via replay do log
- consulta única para operação e gestão (serving)

### Reprocessamento histórico

Quando as regras mudam, temos que reexecutar o pipeline contínuo sobre o histórico de eventos, corrigir eventuais divergências acumuladas no estado atual enquanto que a serving vai passar a expor a nova verdade reconstruída.

**Esse é um dos maiores diferenciais da Kappa**


### Consistência: eventual, não instantânea


O processamento contínuo antecipa informações, o replay confirma/corrige o estado consolidado quando necessário. Pode existir uma diferença "temporária" entre agora e reprocessado. O kappa troca duplicação arquitetural por disciplina em eventos e estado.


### Arquitetura Kappa

**Vantagens:** pipeline único, menor duplicação de lógica que arquiteturas com dois caminhos, reprocessamento por replay sem batch separado, boa adequação a cenários fortemente orientado a eventos.

**Desvantagens:** forte dependência de um backbone de eventos maduro, replays longos podem competir com carga online, exige governança rigorosa de rentenção e schema e o custo pode crescer com armazenamento prolongado de eventos.


### Trade-offs centrais

| Critérios       | Ganho                     | Custo                                |
|-----------------|---------------------------|--------------------------------------|
| Simplicidade    | um pipeline único         | dependência forte do log de eventos  |
| Latência        | respostas rápidas         | operação cuidadosa de estado         |
| Reprocessamento | replay histórico          | tempo/custo em recomputações grandes |
| Evolução        | ajuste contínuo de regras | disciplina de versionamento          |



### Quando usar Kappa

Usamos kappa quando temos a necessidade simultânea de decisões em tempo real e reprocessamento por replay de eventos. Casa muito bem com a cultura de event-driven e operações que priorizam pipeline único e baixa latência.
T

### Quanto evitar Kappa

Precisamos fugir do kappa quando temos um time pequeno sem maturidade operacional em streaming stateful, quando tivermos algum caso de uso com baixa exigência de tempo real ou cenários sem retenção adequada de eventos para replay confiável.


### Confiabilidade e qualidade

Retry com backoff nos consumidores, checkpoints para recuperação de estado, validações de qualidade por completude e consistência, linhagem para rastrear origem e transformação de métricas.

### Segurança e governança

Temos controle de acesso por domínio e sensibilidade ?
Criptografia em trânsito e em repouso
Mascaramento de dados pessoais
Auditoria de consultas e alterações de pipeline.


### Métricas operacionais importantes

Podemos destacar a latência fim a fim (da ingestão até o serving), lag dos consumidores por partição, tempo de replay pra recomputação, divergência entre visão atual e visão reprocessada e a disponibilidade dos endpoints (calculamos o tempo que ele ficou disponível basicamente).

### Comparação entre Kappa x Lambda

| Critério              | Kappa                         | Lambda                    |
|-----------------------|-------------------------------|---------------------------|
| Estrutura             | stream único                  | batch + stream            |
| Reprocessamento       | replay de eventos             | batch histórico           |
| Complexidade operacional | menor topologia            | maior coordenação         |
| Melhor encaixe        | arquitetura event-driven madura | histórico forte + tempo real |

### Conclusão 

Podemos concluir que o **kappa** tenta equilibrar velocidade de resposta, simplicidade arquitetural e capacidade recomputação por replay. 
Funciona bem com  fluxo contínuo de enventos e seu sucesso depende mais da disciplina operacional do que de ferramenta específica.



