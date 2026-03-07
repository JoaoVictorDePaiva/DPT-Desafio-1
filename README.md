# DPT-Desafio-1

Repositório do desafio 1 do projeto "Dados por Todos"
Linkedin do DPT: https://www.linkedin.com/company/dadosportodos/

Especificações técnicas do desafio: https://dadosportodoscommunity.short.gy/01-DESAFIOTECNICO

## Ferramentas: 
Obrigatórias: Google Cloud Storage; BigQuery; Metabase

Irei utilizar de forma adicional: Dataform; Cloud Run; Github

## Detalhamento Técnico:
### Cloud Storage
Considerando a baixa volumetria dos dados (arquivos de até 200 MB), a natureza pontual da extração e a ausência de requisitos para ingestão em streaming, o desenvolvimento de um pipeline automatizado via código ou outro serviço do GCP não se justifica. Neste cenário, a estratégia mais eficiente consiste no upload dos arquivos "à mão". Para a criação do bucket no GCS, optei pelas seguintes configurações: 

Localização: us-central1; Optei por essa single-região pois, para este projeto, não há a necessidade de alta disponibilidade, além de que, dentro do GCP, a us-central é uma das regiões mais baratas, oferecendo tier gratuitos bastante generosos em todas as ferramentas que irei utilizar neste projeto.

Temperatura dos dados: Standard; Como irei utilizar os meus dados de forma quase instantânea no BigQuery, esta era a opção que mais fazia sentido. No final da discussão sobre o GCS irei entrar novamente nessa questão da temperatura.

O restante das configurações, nessa fase inicial, permaneceram os recomendados pela Google.

Antes de partir para o BQ, criei uma regra sobre o ciclo de vida dos dados no meu bucket. Como estimo que irei levar, no máximo, 1 dia para realizar esse desafio, configurei a transição automática dos objetos para a classe de armazenamento Coldline 2 dias após a sua criação dentro do bucket, garantindo uma boa prática de FinOps. Embora o impacto financeiro seja irrisório neste desafio devido à baixa volumetria, é importante criar um habito de realizar boas práticas nas ferramentas que usamos. Vale ressaltar que, em um ambiente produtivo complexo, essa transição não deve ser baseada em estimativas de tempo fixas, no sentido de "prevejo que daqui 2 dias já estará finalizado", mas acredito que, por se tratar de um desafio relativamente "simples", funciona bem neste caso.

<img width="784" height="127" alt="image" src="https://github.com/user-attachments/assets/7ee96228-95a3-4001-b009-8cfc01d5df19" />
