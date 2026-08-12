# 1- Ecossistema de Big Data

### Ecossistema = pessoas + processos + tecnologia

Pessoas: engenharia, analytics, produto, segurança, compliance
- **OBS:** Quem vai resolver o problema

Processos: contrato de dados, qualidade, deploy, monitoramento
- **OBS:** Pra CC basicamente é ligar 2 da manhã pra avisar que o server caiu

Tecnologia: ingestão, storage, processamento, consumo
- **OBS:** As tecnologias que existem e tentam resolver esses problemas (mongo, postgrees etc)


### Ciclo de vida de dados

> geração → ingestão → armazenamento → processamento → consumo → governança

Cada etapa tem custo, risco e requisito de desempenho.

- Lembrando do exemplo da presença, tem um custo baixo, risco baixo e um requisito de desempenho raoável

O desenho correto evita retrabalho e gargalos futuros.

- Basicamente a parte mais importante do sistema é o design.


### Bloco 1 — Fontes de dados

Aplicações transacionais

Logs de sistemas e observabilidade

APIs externas e parceiros

> Alguém pode te fornecer o dado via API, mas quem decide o que fazer com eles é você.

Eventos de negócio (ex.: transação aprovada/negada)

### Bloco 2 — Ingestão

Batch: carga periódica (hora/dia)
> Como era antigamente, alguém da secretaria marcava a presença depois de receber a lista

Stream: fluxo contínuo de eventos
> Como é hoje, feito via aplicativo e gerando eventos que podem ser consumidos/reprocessados por outras partes do sistema.

Objetivo: mover dados com confiabilidade e rastreabilidade



### Bloco 3 — Armazenamento

Data Lake: bruto, escalável, baixo custo
- **OBS:** Dado bruto, era o que o Renan queria fazer na Fixee (da pra usar S3 e etc), teria que escalar e basicamente temos que combinar o formato que ele virá pra facilitar a vida. Basicamente é um grande google drive armazenando diversos arquivos

Data Warehouse: modelado para análise

Lakehouse: combinação de lake + governança/consulta

### Bloco 4 — Processamento

Batch processing: transformações em lote
> Exemplo da copa do mundo, pra saber quem é o melhor jogador e preciso analisar tudo no final ao invés de analisar no primeiro jogo.

Stream processing: cálculo contínuo em tempo real
> Lembra do exemplo do Uber, não adianta achar motorista quando eu já to em casa. 

Frameworks distribuídos para paralelismo e escala



### Bloco 5 — Consumo

BI e dashboards
- **OBS:** Cuidado pra não rodar a query a cada segundo e pesar o sistema (tempo real)

Modelos de ML
- **OBS:** Se o dado veio errado pra treinar o modelo, já era.

APIs de dados para aplicações

Alertas operacionais em tempo real
- **OBS:** Aquele exemplo de clonarem seu cartão, o aviso que tão tentando fazer uma compra em naquele momento tem que vir em tempo real, não adianta em avisar no dia seguinte



### Bloco 6 — Governança, segurança e observabilidade

Catálogo, linhagem e ownership
Controle de acesso e criptografia
Monitoramento de pipelines e SLAs
Qualidade de dados (completude, consistência, pontualidade)



### Batch x Stream (quando usar)

Batch: custo menor, alta capacidade, maior latência
Stream: baixa latência, resposta imediata, maior complexidade
Regra prática:
se decisão pode esperar, batch pode bastar;
se decisão precisa ser imediata, stream é necessário.

> Lembra novamente do exemplo do melhor jogador da copa (batch) e do pedido de uber (stream)


