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
Após obtenção do dataset disponibilizado via API em formato JSON, foi realizado uma exploração preliminar para compreendê-los, assim como um tratamento dos dados originais para as futuras análises. 

* [Notebook da Semana 1
](https://raw.githubusercontent.com/jackson-simionato/challenge_alura_DS01/main/week_1_challenge_alura_DS_2022_05.ipynb)

Um dicionário das colunas foi disponibilizado:

#### Descrição das colunas
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

A maioria das colunas são variáveis categóricas, mas também ocorrem variáveis numéricas. Alguns dos processamentos aplicados estão listados abaixo:
* Todas os nomes de colunas e valores de variáveis foram traduzidos para o português;
* Análise de inconsistências em todos os atributos (ex: valores nulos, tipo de dado incorreto, etc.);
* Correções de inconsistências em três colunas do dataset (churn, idoso e cobranca_total);
* Nova coluna criada para representar o gasto diário de cada cliente (cobranca_diaria).

## Semana 2
Com a finalização do pré-processamento da base de dados, a análise se voltou à exploração dos dados e geração de gráficos para obter *insights*.

* [Notebook da Semana 2] (https://github.com/jackson-simionato/challenge_alura_DS01/blob/main/week_2_challenge_alura_DS_2022_05.ipynb)

* **Distribuição da variável target (churn):** a taxa de churn está em patamar bastante elevado, cerca de 26% dos usuários.

![image](https://user-images.githubusercontent.com/40372626/174589405-1e0dfe3f-07d6-428c-81c2-2ba6c1b5bde2.png)

### Taxa de churn e variáveis numéricas
* **Relação entre taxa de churn e meses de contrato:** um padrão bastante interessante foi percebido nesta análise: a maioria dos clientes que cancelaram os serviços da Alura Voz o fizeram logo nos primeiros meses de contrato com a empresa. Portanta há uma dificuldade em fidelizar os clientes.

![image](https://user-images.githubusercontent.com/40372626/174906166-d2435a51-5028-4a88-91f5-7f16bca3f583.png)

Ao detalhar essa análise incluindo variáveis categóricas como idade, gênero e existência de dependentes, pode-se traçar um perfil genérico dos clientes que cancelam a assinatura da Alura Voz nos primeiros meses de serviço: pessoas mais jovens e sem dependentes, provavelmente jovens solteiros, sem distinção de gênero.

![image](https://user-images.githubusercontent.com/40372626/174904366-6460e974-134f-4a1e-912f-e04f686825ae.png)

### Taxa de churn e variáveis categóricas

* **Relação entre taxa de churn, gênero e idade:** o gênero dos clientes está distribuído em duas partes praticamente perfeitas e, aleḿ disso, a taxa de churn não varia conforme o gênero dos clientes. Por outro lado, clientes com mais de 65 anos são minoria no total de clientes, porém representam a maioria dos clientes que cancelaram os serviços da Alura Voz.

![image](https://user-images.githubusercontent.com/40372626/174906240-8f8b9733-b74b-4567-85e7-9709bf416b04.png)

* **Relação entre taxa de churn, dependentes e parceiro:** no geral, foi verificado uma tendência da taxa de churn ser maior em consumidores **sem dependentes e sem parceiros**. Uma interpretação possível é que pessoas solteiras tendem a ser mais jovens e não possuem grande estabilidade financeira, desta forma pequenas variações nos preços e qualidade dos serviços prestados já são suficientes para aumentar a taxa de churn nesse grupo de pessoas.

<img src="https://user-images.githubusercontent.com/40372626/174906316-69c2a767-925c-4b63-a109-923fb4ca6341.png" width="445"/> <img src="https://user-images.githubusercontent.com/40372626/174906352-d12bf9f7-e990-49e0-b00e-2451806b3b47.png" width="445"/> 

* **Relação entre taxa de churn e o tipo de internet contratado:** ficou evidente que a taxa de churn é maior em clientes que contrataram fibra ótica, possivelmente esta modalidade de seviço não esta agradando os clientes
![image](https://user-images.githubusercontent.com/40372626/174594805-fa3653ab-9537-447e-85ad-d017d47f604e.png)

* **Relação entre taxa de churn e a contratação de serviços adicionais de segurança:** nesta etapa foi analisado como a contratação de serviços adicionais está impactando a taxa de churn. Em todos os casos os serviços parecem agradar os cleintes contratantes, já que a taxa de churn é relativamente maior nos clientes que não contrataram estes servços.
![image](https://user-images.githubusercontent.com/40372626/174906516-90e57de1-5a46-4765-9c5a-bffbca97a473.png)

* **Relação entre taxa de churn e variáveis contratuais:** com relação às variáveis contratuais e de forma de pagamento, alguns padrões bem claros foram identificados: a taxa de churn é proporcionalmente maior em clientes que optaram por receber a fatura online, que firmaram contratos mensais e que tem o cheque eletrônico como forma de pagamento.
![image](https://user-images.githubusercontent.com/40372626/174904581-4b4dba0a-fd9e-4e1f-90c4-4e05e2ebe1fa.png)

![image](https://user-images.githubusercontent.com/40372626/174904649-ec9d2b47-8010-4147-8fed-b6f8e527d389.png)

![image](https://user-images.githubusercontent.com/40372626/174904589-7b4b2837-9b61-4d61-9e3e-86228f16eba3.png)

