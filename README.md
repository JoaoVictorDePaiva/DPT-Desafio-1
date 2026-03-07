# DPT-Desafio-1

Repositório do desafio 1 do projeto "Dados por Todos"
Linkedin do DPT: https://www.linkedin.com/company/dadosportodos/

Especificações técnicas do desafio: https://dadosportodoscommunity.short.gy/01-DESAFIOTECNICO

## Ferramentas: 
Obrigatórias: Google Cloud Storage; BigQuery; Metabase

Irei utilizar de forma adicional: Dataform; Cloud Run; Github

## Detalhamento Técnico:
### Cloud Storage
Considerando a baixa volumetria dos dados (arquivos de até 200 MB), a natureza pontual da extração (sem necessidade de cargas recorrentes) e a ausência de requisitos para ingestão em streaming, o desenvolvimento de um pipeline automatizado via código ou outro serviço do GCP não se justifica. Neste cenário, a estratégia mais eficiente consiste no upload dos arquivos "à mão". Para a criação do bucket no GCS, optei pelas seguintes configurações: 

Localização: us-central1; Optei por essa single-região pois, para este projeto, não há a necessidade de alta disponibilidade, além de que, dentro do GCP, a us-central é uma das regiões mais baratas, oferecendo tier gratuitos bastante generosos em todas as ferramentas que irei utilizar neste projeto.

Temperatura dos dados: Standard; Como irei utilizar os meus dados de forma quase instantânea no BigQuery, esta era a opção que mais fazia sentido. No final da discussão sobre o GCS irei entrar novamente nessa questão da temperatura.

O restante das configurações, nessa fase inicial, permaneceram os recomendados pela Google.
