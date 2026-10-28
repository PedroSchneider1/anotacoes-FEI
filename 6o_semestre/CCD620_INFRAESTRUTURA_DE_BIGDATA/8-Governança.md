\# Governança em Big Data

\---



\### Objetivos:



A ideia é saber explicar o que é governança de dados e por que é critica em ambientes de big data;

Descrever os pilares: \*\*pessoas, processos e tecnologia\*\*

Apresentar a \*\*LGPD\*\* e a \*\*GDPR\*\*

Reconhecer as leis de proteção de dados de outros países e regras de transferência internacional.





\### Por que Governança importa?



Como Big Data concentra volumes gigantes de dados de várias fontes, precisamos estar preparados para lidar com os riscos (quanto mais dados, mais risco).



> As leis de proteção de dados passaram a exigir prova de governança





\### O que acontece sem governança?



Ninguém sabe onde está cada dado, cópias soltas em planilhas, buckets e notebooks pessoais e etc.



Resumo: Ninguém sabe onde está nada, ninguém é dono de nada e tudo é correria e improviso.



\### Definição



Governança de dados é o conjunto de políticas, papéis, processos e tecnologias que garantem que os dados sejam:



Corretos e confiáveis. acessíveis pra quem precisa, protegidos contra uso indevido e tratados conforme leis e regulamentos.



> Governança = regras claras + responsáveis definidos + execução contínua



\### Governança x Gestão de Dados



O \*\*gestor\*\* executa, "como fazemos funcionar?"



A governança define regras e processos, "quem decide e por quê"?



\### Pilares da governança



\*\*Pessoas, Processos e Tecnologia\*\*



\*\*Pessoas\*\* -> Papéis definidos, comitês e fóruns de decisão, treinamento e cultura de dados



\*\*Processos\*\* -> Políticas de uso, acesso e retenção, resposta a incidentes e a titulares.



\*\*Tecnologia\*\* -> Catálogo e linhagem, monitoramento e policies as code.





\### Dimensões da governança







\### Papéis e Responsabilidades



\- Data Owner -> Dono do dado, cara chato que aprova os acessos



\- Data Steward -> Cara da qualidade, documentação e metadados no dia a dia.



\- Encarregado (DPO) -> Faz a ponte com titulares e autoridades (LGPD/GDPR)



\- Chief Data Officer (CDO)-> Define estratégia e políticas de dados



\- Comitê de governança -> Fórum que aprova políticas e resolve conflitos





\### Metadados e catálogo de dados



Metadado: Dado sobre dado



Catálogo de dados: inventário pesquisável dos ativos de dados



Funções do catálogo: descoberta, documentação, classificação, linhagem e impacto de mudanças





\### Linhagem de dados



Responde a pergunta: "se eu mudar essa tabela, o que quebra?"



Isso é essencial para auditoria e regulação, análise de impacto de mudanças de schema, atendimento a direitos de titulares.



Pode ser capturada automaticamente por ferramentas integradas ao pipeline





\### Qualidade de dados





Dimensões classicas:



| Dimensão | Pergunta |

| --- | --- |

| Completude | Falta algum registro ou campo? |

| Consistência | O dado bate entre sistemas? |

| Acurácia | O valor reflete a realidade? |

| Pontualidade | Chegou dentro do SLA? |

| Unicidade | Existem duplicados? |

| Validade | Respeita formato e domínio? |





\### Classificação de dados



Níveis típicos:



Dados públicos -> Pode ser divulgado

Interno -> Uso restrito à empresa

Confidencial -> Acesso por necessidade

Sensível/Restrito -> Dado pessoal sensível, segredo bancário





> A classificação define: criptografia, mascaramento, retenção e quem acessa. Deve ser registrada no catálogo como tag do ativo.





\### Ciclo de vida dos dados



\*\*Coleta -> Armazenamento -> Uso -> Compartilhamento -> Arquivamento -> Descarte\*\*



Cada uma dessas fases tem suas próprias regras:



Coleta: Mínimo necessário e com base legal;

Armazenamento: Criptografia e camada adequada;

Uso: Finalidade declarada;

Descarte: Eliminação ou anonimização ao fim da retenção





\### Segurança



Auditoria de acesso: quem acessou o quê, quando e por quê.



Mascaramento de dados pessoais em ambientes analíticos e de

desenvolvimento.



\### Privacidade: conceitos-chave



Dados pessoal: informação que identifica uma pessoa (nome, cpf etc)



Dado sensível: Origem racial, biometria, política, saúde



Anonimização: remove a possibilidade de identificação de forma irreversível



Pseudonimização: substitui identificadores (dá pra reverter com chave separada)



> Atenção: Dados " soltos" combinados podem reidentificar pessoas (ex.: CEP + Data de Nascimento + Gênero)





\### Privacy by design



Privacidade desde a concepção do sistema, não remendada depois.



Medidas práticas: 



Minimização -> Coletar só o necessário;

Finalidade explícita -> Usar só para o que foi declarado;

Separação de identificadores em ambientes analíticos;

Avaliação de impacto para tratamentos de alto risco;

Descarte planejado desde o início.







\### LGPD



Cara, acabou aqui. Se quiser revisar lê os slides O.o

