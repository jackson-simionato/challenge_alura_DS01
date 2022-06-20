![image](https://user-images.githubusercontent.com/40372626/172276528-0debe6ed-8d19-4a76-8ecc-1723d1db894d.png)

# Alura Voz - Challenge Data Science (2022.05.01)

Projeto voltado para solução e compartilhamento do Challenge Alura de Data Science 01, realizado no mẽs de maio de 2022!

**Python** foi a linguagem utilizada no desenvolvimento, utilizando Jupyer Notebooks para apresentar os resultados. Os principais pacotes utilizados foram:
* pandas
* numpy
* plotly
* seaborn
* scikit-learn
* imbalanced-learn

## Objetivo

Você foi contratado(a) como cientista de dados pela operadora de telecomunicações **Alura Voz**. Na reunião inicial com as pessoas responsáveis pela área de vendas da empresa, foi explicada a importância de se **reduzir a Taxa de Evasão** de Clientes, conhecido como **Churn Rate**. Basicamente, o Churn Rate indica o quanto a empresa perdeu de receita ou clientes em um período de tempo. Com sua experiência, você sugere, como passo inicial, a identificação de clientes que teriam uma maior chance de deixar a empresa. 

Assim, o desafio tem como objetivo utilizar conceitos de Data Science para explorar, tratar e modelar uma base de dados de clientes da **Alura Voz**. Com isso, serão testadas hipóteses para dscrever o padrão de ocorrência de **Churn** com relação às outras variáveis disponíveis. No total serão 4 semanas de desafio.

* [Base de dados original
](https://raw.githubusercontent.com/sthemonica/alura-voz/main/Dados/Telco-Customer-Churn.json)

## Semana 1: aquisição, limpeza e tratamento dos dados
Após obtenção do dataset disponibilizado via API em formato JSON, foi realizado uma exploração preliminar para compreendê-los. Um dicionário das colunas foi disponibilizado:

#### Dicionário dos dados
* `customerID`: número de identificação único de cada cliente
* `Churn`: se o cliente deixou ou não a empresa 
* `gender`: gênero (masculino e feminino) 
* `SeniorCitizen`: informação sobre um cliente ter ou não idade igual ou maior que 65 anos 
* `Partner`:  se o cliente possui ou não um parceiro ou parceira
* `Dependents`: se o cliente possui ou não dependentes
* `tenure`:  meses de contrato do cliente
* `PhoneService`: assinatura de serviço telefônico 
* `MultipleLines`: assisnatura de mais de uma linha de telefone 
* `InternetService`: assinatura de um provedor internet 
* `OnlineSecurity`: assinatura adicional de segurança online 
* `OnlineBackup`: assinatura adicional de backup online 
* `DeviceProtection`: assinatura adicional de proteção no dispositivo 
* `TechSupport`: assinatura adicional de suporte técnico, menos tempo de espera
* `StreamingTV`: assinatura de TV a cabo 
* `StreamingMovies`: assinatura de streaming de filmes 
* `Contract`: tipo de contrato
* `PaperlessBilling`: se o cliente prefere receber online a fatura
* `PaymentMethod`: forma de pagamento
* `Charges.Monthly`: total de todos os serviços do cliente por mês
* `Charges.Total`: total gasto pelo cliente

A maioria das colunas são variáveis categóricas, mas também ocorrem variáveis numéricas. Todas os nomes de colunas e valores de variáveis foram traduzidos para o português, além disso cada atributo foi validado individualmente com o objetivo de identificar possíveis inconsistências como valores nulos, variáveis numéricas formatadas como string, padronização na nomenclatura de valores categóricos, etc.

Por fim, uma nova coluna foi criada para representar o gasto diário de cada cliente.

* [Notebook da Semana 1
](https://raw.githubusercontent.com/jackson-simionato/challenge_alura_DS01/main/week_1_challenge_alura_DS_2022_05.ipynb)

## Semana 2
Com a finalização do pré-processamento da base de dados, a análise se voltou à exploração dos dados e geração de gráficos para obter *insights*.

* **Distribuição da variável target (churn):** a taxa de churn está em patamar bastante elevado, cerca de 26% dos usuários.
![image](https://user-images.githubusercontent.com/40372626/174589405-1e0dfe3f-07d6-428c-81c2-2ba6c1b5bde2.png)

* **Relação entre taxa de churn, gênero e idade:** o gênero dos clientes está distribuído em duas partes praticamente perfeitas e, aleḿ disso, a taxa de churn não varia conforme o gênero dos clientes. Por outro lado, clientes com mais de 65 anos são minoria no total de clientes, porém representam a maioria dos clientes que cancelaram os serviços da Alura Voz.
![image](https://user-images.githubusercontent.com/40372626/174590393-f646325b-b40a-4888-9f3e-d2130c0f643f.png)


* **Relação entre taxa de churn, dependentes e parceiro:** no geral, foi verificado uma tendência da taxa de churn ser maior em consumidores **sem dependentes e sem parceiros**. Uma interpretação possível é que pessoas solteiras tendem a ser mais jovens e não possuem grande estabilidade financeira, desta forma pequenas variações nos preços e qualidade dos serviços prestados já são suficientes para aumentar a taxa de churn nesse grupo de pessoas.

<img src="https://user-images.githubusercontent.com/40372626/174592618-d7bb93d1-dd28-4fdc-b552-899c7e94c2e7.png" width="525"/> <img src="https://user-images.githubusercontent.com/40372626/174592645-f0094e55-5560-4999-84d0-b24d2fd7bd0e.png" width="525"/> 
