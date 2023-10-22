# Projeto de Conclusão da Disciplina "Data Analytics" do MBA em Data Science
<p align="right">Outubro/2023</p>

---

## Índice

<!--ts-->
   * [Descrição do Projeto](https://github.com/adriana-takahagui/mba-data-analytics#descrição-do-projeto)
   * [Descrição do Problema de Negócio](https://github.com/adriana-takahagui/mba-data-analytics#descrição-do-problema-de-negócio)
   * [Dicionário de Variáveis](https://github.com/adriana-takahagui/mba-data-analytics#dicionário-de-variáveis)
   * [Metodologia](https://github.com/adriana-takahagui/mba-data-analytics#metodologia)
   * [Desenvolvimento](https://github.com/adriana-takahagui/mba-data-analytics#desenvolvimento)
     * [Preparação dos dados](https://github.com/adriana-takahagui/mba-data-analytics#preparação-dos-dados)
     * [Tratamento dos Dados no Power Query Editor]()
     * [Relacionamento das Tabelas]()
     * [Relatórios e Insights]()
   * [Próximos Passos]()
   * [Fontes e Referências](https://github.com/adriana-takahagui/mba-data-analytics#fontes-e-refer%C3%AAncias)
<!--te-->


---

## Descrição do Projeto

**Disciplina**: Data Analytics 

**Requisitos**: 

- [X] Objetivo: deve ser bem definido o objetivo do projeto e qual problema de negócio será resolvido.
- [X] Resolver o problema de negócio com aplicação dos conhecimentos dos módulos da disciplina Data Analytics. 
- [X] Tema Livre, preferencialmente um problema corriqueiro da empresa ou área em que atua.
- [X] Power BI: deve-se construir um dashboard em Power BI.
- [ ] Python: O dashboard em Power BI deve conter no mínimo um gráfico construído com o Python. O Data Wrangling pode-se utilizar o Python.

---

## Descrição do Problema de Negócio

Esta seção aborda a descrição do problema de negócio escolhido para desenvolver o projeto da disciplina "Data Analytics".

**Tema**:

- Análise de _Customer Service_, _Customer Experience_ e _Customer Satisfaction_ em uma empresa de e-Commerce.

**Objetivo**:

- Melhorar o relacionamento com o cliente em todo o processo de venda, fortalecer a marca com maior presença no mercado, capturar as necessidades do cliente, e melhorar a sua satisfação, tudo isso focando na análise do atendimento ao cliente (_customer service_) e de sua experiência e satisfação na jornada de compra.

**Problema de Negócio**:

- Como toda empresa de e-commerce, a "Online Shopping Harbor"[^1] (nome da empresa fictícia para este projeto) também precisa lidar com o processo de pós venda de seus produtos.
- Assim, a "Online Shopping Harbor" deve ser capaz não somente de atender seus clientes da melhor maneira possível como também inovar com uso de tecnologia, análise de dados e inteligência artificial para que possa sobreviver em um mercado cada vez mais competitivo.
- E para alcançar isso, percebeu-se a necessidade de **_melhorar seu atendimento ao cliente_** para que este possa ter uma **_melhor experiência e satisfação_** na sua jornada e, assim, retornar em outras compras e se tornar um promotor da marca da "Online Shopping Harbor", resultando no aumento da retenção do cliente. 
- Para tanto, uma dashboard em Power BI foi desenvolvido para analisar o problema proposto. 

**Fontes de Dados**:

- Uma amostra aleatória dos dados utilizados na construção deste dashboard foi extraída de um e-commerce abrangendo o período de 2022. Depois, os dados foram anonimizados, tratados e filtrados retirando qualquer aspecto desse e-commerce.    
- Portanto, qualquer semelhança com qualquer cenário de qualquer empresa é pura coincidência. 
- O conjunto de dados em questão é formado pelos arquivos abaixo:
  - **dados_chamados_2022.xlsx**: dados com chamados de atendimento ao cliente 
  - **dados_nps_2022.xlsx**: dados com avaliações da pesquisa NPS
  - **dados_rfv_2022.xlsx**: dados necessários para análise de segmentação de cliente (RFV)
  - **dados_clientes.xlsx**: dados de cadastro de clientes
  - **dados_categoria_produtos.xlsx**: dados de cadastro de categorias e departamentos dos produtos disponibilizados pela "Online Shopping Harbor"

**Link do Dashboard no Power BI**: 

---

## Dicionário de Variáveis

Esta seção descreve as tabelas e as variáveis utilizadas no projeto e no problema proposto.

**Descrição das variáveis com origem em: dados_chamados_2022.xlsx**

|  N |       Variável       | Tipo do Dado |                              Descrição                             |                          Valores Permitidos                          |
|:--:|:--------------------:|:------------:|:------------------------------------------------------------------:|:--------------------------------------------------------------------:|
|  1 | id_protocolo         |    String    | Identificador alfanumérico único do chamado                        | Não enumerado                                                        |
|  2 | id_cliente           |    String    | Identificador alfanumérico único do cliente                        | Não enumerado                                                        |
|  3 | id_compra            |    String    | Identificador alfanumérico único da compra                         | Não enumerado                                                        |
|  4 | id_entrega           |    String    | Identificador alfanumérico único da entrega                        | Não enumerado                                                        |
|  5 | data_criacao         |  Data e Hora | Data e hora de criação do chamado de atendimento                   | Formato: dd/mm/aaaa hh:mm                                            |
|  6 | data_encerramento    |  Data e Hora | Data e hora do encerramento do chamado de atendimento              | Formato: dd/mm/aaaa hh:mm                                            |
|  7 | id_canal             |    Inteiro   | Identificador do canal de atendimento                              | Número inteiro entre 0 e 8                                           |
|  8 | tipo_chamado         |    String    | Tipo do chamado                                                    | Reativo; Especial                                                    |
|  9 | id_motivo_cliente_n3 |    Inteiro   | Identificador numérico do motivo do chamado de atendimento         | Número inteiro entre 1 a 20, mas novos motivos podem ser adicionados |
| 10 | unidade_negocio      |    String    | Unidade de negócio                                                 | B2C; B2B; Marketplace                                                |
| 11 | modelo_venda         |    String    | Modelo de Venda                                                    | 1P; 3P                                                               |
| 12 | status_chamado       |    String    | Status do chamado                                                  | Resolvido; Não resolvido                                             |
| 13 | recontatos           |    Inteiro   | Quantidade de recontatos realizados pelo cliente neste chamado     | Não enumerado                                                        |
| 14 | reaberturas          |    Inteiro   | Quantidade de reaberturas deste chamado                            | Não enumerado                                                        |
| 15 | id_categoria_produto |    Inteiro   | Identificador numérico da categoria do produto                     | Não enumerado                                                        |
| 16 | valor_venda_unidade  |    Decimal   | Valor unitário de venda do produto adquirido                       | Não enumerado                                                        |
| 17 | valor_frete          |    Decimal   | Valor do frete do produto adquirido                                | Não enumerado                                                        |
| 18 | id_status_entrega    |    Inteiro   | Identificador numérico do status da entrega                        | 1 - Cancelado; 2 - Devolução; 3 - Entregue ao Cliente                |
| 19 | data_compra          |     Data     | Data da compra                                                     | Formato: dd/mm/aaaa                                                  |
| 20 | data_estimada        |     Data     | Data estimada de entrega informada ao cliente no momento da compra | Formato: dd/mm/aaaa                                                  |
| 21 | data_entrega         |     Data     | Data da entrega realizada                                          | Formato: dd/mm/aaaa                                                  |

**Descrição das variáveis com origem em: dados_nps_2022.xlsx**

| N |     Variável     | Tipo do Dado |                                        Descrição                                       |      Valores Permitidos     |
|:-:|:----------------:|:------------:|:--------------------------------------------------------------------------------------:|:---------------------------:|
| 1 | id_nps           |    String    | Identificador alfanumérico único da pesquisa NPS                                       | Não enumerado               |
| 2 | id_entrega       |    String    | Identificador alfanumérico único da entrega                                            | Não enumerado               |
| 3 | id_cliente       |    String    | Identificador alfanumérico único do cliente                                            | Não enumerado               |
| 4 | data_pesquisa    |     Data     | Data de realização da pesquisa NPS                                                     | Formato: dd/mm/aaaa         |
| 5 | data_avaliacao   |     Data     | Data de avaliação da pesquisa NPS pelo cliente                                         | Formato: dd/mm/aaaa         |
| 6 | avaliacao        |    Inteiro   | Nota de avaliação dada pela entrega do pedido                                          | Número inteiro entre 0 a 10 |
| 7 | origem           |    String    | Origem da pesquisa NPS                                                                 | E-mail; SMS                 |
| 8 | chamado_atrelado |   Booleano   | Indicador se a entrega vinculada à pesquisa NPS tem um chamado de atendimento atrelado | 1 - Sim; 0 - Não            |

**Descrição das variáveis com origem em: dados_rfv_2022.xlsx**

| N |      Variável      | Tipo do Dado |                                     Descrição                                    |                   Valores Permitidos                   |
|:-:|:------------------:|:------------:|:--------------------------------------------------------------------------------:|:------------------------------------------------------:|
| 1 | id_cliente         |    String    | Identificador alfanumérico único do cliente                                      | Não enumerado                                          |
| 2 | ano                |    Inteiro   | Ano da data da compra                                                            | Formato do ano com 4 dígitos                           |
| 3 | mes                |    Inteiro   | Mês da data da compra                                                            | Formato do mês em dígitos, ou seja, entre 1 a 12       |
| 4 | id_status_entrega  |    Inteiro   | Identificador do status da entrega                                               | 1 - Cancelado; 2 - Devolução; 3 - Entregue ao Cliente  |
| 5 | qtd_pedidos        |    Inteiro   | Quantidade de pedidos realizado no período indicado pelo Ano e Mês               | Não enumerado                                          |
| 6 | total_faturamento  |    Decimal   | Total de faturamento realizado no período indicado pelo Ano e Mês                | Não enumerado                                          |
| 7 | data_ultima_compra |     Data     | Data da última compra realizada no período indicado pelo Ano e Mês               | Formato: dd/mm/aaaa                                    |
| 8 | chamado_atrelado   |   Booleano   | Indicador se a entrega vinculada à compra tem um chamado de atendimento atrelado | 1 - Sim; 0 - Não                                       |

**Descrição das variáveis com origem em: dados_clientes.xlsx**

| N |   Variável   | Tipo do Dado |                  Descrição                  |                                           Valores Permitidos                                           |
|:-:|:------------:|:------------:|:-------------------------------------------:|:------------------------------------------------------------------------------------------------------:|
| 1 | id_cliente   |    String    | Identificador alfanumérico único do cliente | Não enumerado                                                                                          |
| 2 | nome_cliente |    String    | Nome do cliente                             | Dado anonimizado e vinculado a números inteiros entre 10001 e 67392, porém novos clientes podem surgir |
| 3 | perfil       |    String    | Perfil do cliente                           | PF (Pessoa Física); PJ (Pessoa Jurídica)                                                               |
| 4 | municipio    |    String    | Município de localização do cliente         | Conjunto contendo apenas os municípios do Brasil                                                       |
| 5 | estado       |    String    | Estado de localização do cliente            | Conjunto contendo apenas os 26 estados do Brasil                                                       |
| 6 | estado_sigla |    String    | Sigla do estado de localização do cliente   | Conjunto contendo apenas os 26 estados do Brasil formado por 2 caracteres                              |
| 7 | regiao       |    String    | Região de localização do cliente            | 5 regiões do Brasil (Sudeste; Nordeste; Norte; Centro-Oeste; Sul)                                      |
| 8 | pais         |    String    | País de localização do cliente              | Brasil                                                                                                 |

**Descrição das variáveis com origem em: dados_categoria_produtos.xlsx**

| N |       Variável       | Tipo do Dado |                 Descrição                |                Valores Permitidos               |
|:-:|:--------------------:|:------------:|:----------------------------------------:|:-----------------------------------------------:|
| 1 | id_categoria_produto |    Inteiro   | Identificador numérico único do produto  | Não enumerado                                   |
| 2 | departamento_produto |    String    | Departamento a que pertence o produto    | Não enumerado. Novos departamentos podem surgir |
| 3 | categoria_produto    |    String    | Categoria a que pertence o produto       | Não enumerado. Novas categorias podem surgir    |

---

## Metodologia

**1. Entendimento do negócio** <br/>
**Qual a necessidade ou dor do negócio?**
- O case abordado é um e-commerce que vende online diversos tipos de produtos, tanto para consumidores (B2C) quanto para empresas (B2B), possuindo mais de 1.230 categorias de produtos e tendo atuação em todas as 5 regiões do Brasil. Para este projeto, foi extraída uma amostra aleatória de dados abrangendo o período de um ano (2022) e contendo dados de compras de clientes, chamados de atendimento e pesquisa NPS. 
- Neste processo, o consumidor realiza uma compra no site da “Online Shopping Harbor”. Em seguida, realiza o pagamento, e uma data estimada de entrega é apresentada no momento da compra. Tudo seguindo o fluxo normal, a entrega é realizada no endereço indicado. Caso o consumidor tenha qualquer dúvida ou necessite de informações, solicitações ou para realizar qualquer reclamação, ele abre um chamado com a Online Shopping Harbor através dos diversos canais de atendimento como site, email, telefone, app, entre outros. 
- O principal objetivo deste projeto é criar uma análise sobre a performance de atendimento do cliente da "Online Shopping Harbor" no Power BI como apresentado no item “Descrição do Problema de Negócio”. 

**2. Entendimento dos dados** <br/>
**Quais dados estão presentes / são necessários? Os dados estão disponíveis, preparados e tratados?**
- Esta fase envolve olhar os dados disponíveis com cuidado, entendê-los e prepará-los de tal forma que atenda às necessidades de análise proposta e construção do dashboard. Aqui, somente tabelas disponíveis e de interesse foram utilizadas. 

**3. Preparação dos dados** <br/>
**Como os dados foram tratados e preparados para o dashboard?**
- Após o entendimento dos dados, a próxima fase é a preparação dos dados, uma fase muito importante e que toma bastante tempo. Ela é formada por diversas etapas como: transformação dos dados, criação de novas variáveis, agrupamento de dados, entre outras. 
- Nesta fase, foi retirada a amostra aleatória com os dados anonimizados, sumarizados e contemplando o problema proposto. 
- Depois disso, alguns tratamentos foram realizados no Power Query Editor. 

**4. Realização de cálculos para Análise** <br/>
**Quais as medidas e cálculos necessários para análise?**
- Esta fase envolve a criação de medidas DAX para atender as análises e indicadores que irão compor o Dashboard. Aqui, diversas medidas e cálculos foram criados para:
  - Indicadores de chamados de atendimento
  - NPS
  - Segmentação de clientes através da análise RFV

**5. Storytelling** <br/>
**Qual a história por trás dos dados?**
- Esta fase é formada pela elaboração do layout do dashboard e storytelling com dados, dispondo os visuais de tal forma que contem uma história, assim como utilizando os diversos recursos visuais da ferramenta e as possibilidades de design para facilitar a leitura das informações e extração de insights. 

**6. Implementação** <br/>
**Como o dashboard será disponibilizado e os dados atualizados?**
- Uma vez que o dashboard esteja validado e homologado pela área de negócio que irá utilizar no dia a dia, o dashboard poderá ser publicado em uma workspace no Serviço do Power BI e disponibilizado para os usuários finais. 
- Para atualização dos dados, será necessária a instalação de um gateway, caso os arquivos estejam localizados em um servidor local. Caso estejam armazenados na nuvem como uma pasta no SharePoint Online, o gateway não será necessário. 
- A partir daí, uma atualização agendada pode ser configurada para ocorrer diariamente ou conforme a necessidade da área de negócio. 

**7. Acesso ao dashboard** <br/>
**Como a área de negócio irá acessar o resultado (dashboard)?**
- Uma vez que o dashboard esteja disponibilizado, a área de negócio poderá acessá-lo diariamente no Serviço online do Power BI pelo link https://app.powerbi.com/, logando com seu usuário e senha. 
- O dashboard também poderá ser embedado em um portal ou intranet da empresa "Online Shopping Harbor", facilitando o acesso rápido. 

---

## Desenvolvimento e Explicações 

Esta seção aborda o desenvolvimento e as explicações de cada relatório desenvolvido para resolver o problema proposto.

### Preparação e Tratamento dos Dados


### Relacionamento das Tabelas


### Relatórios e Explicações

Este dashboard é formado por 6 páginas:
- Página Inicial
- Chamados
- Análise RFV
- NPS
- Correlação & Outliers
- Recomendações

### Insights 

--- 

## Próximos Passos 

---

## Fontes e Referências

Esta seção disponibiliza as fontes e as referências utilizadas para o desenvolvimento do projeto e resolução do problema proposto. 

[^1]: Nome escolhido com uso do ChatGPT
