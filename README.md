# ProjetoMachineLearning
Repositório para realizar o projeto solicitado no curso da DIO AI-900

# Madson Ferrari

Olá pessoal, eu sou Madson Ferrari, Engenheiro eletricista, pós graduado em Mecatrônica pela UFRJ e entusiasta pela área de informática, programação e Innovation

## Você pode me encontrar aqui:

[![Perfil DIO](https://img.shields.io/badge/-Meu%20Perfil%20na%20DIO-0077B5?style=for-the-badge&logo=gitbook&logoColor=white)](https://www.dio.me/users/madson_ferrari)

[![LinkedIn](https://img.shields.io/badge/-LinkedIn-000?style=for-the-badge&logo=linkedin&logoColor=30A3DC)](https://www.linkedin.com/in/MadsonFerrari/)

[![Youtube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@MadsonFerrari)

# DIO-Machine-Learning

# Projeto de Aprendizado de Máquina (PT)

- A primeira etapa foi assitir ao curso de ML da plataforma DIO dentro do bootcamp AI-900
- Aprender os conceitos de ML e usar a plataforma da Azure para testar um modelo de ML
- Buscar dados para realizar o projeto final deste módulo
- Eu usei como base a data Flair [Data Flair Site](https://data-flair.training/blogs/machine-learning-datasets/)
- Dentre vários Datasets, eu escolhi o de Clientes de Shopping.
- O conjunto de dados dos clientes do shopping contém informações sobre pessoas que visitam o shopping. O conjunto de dados tem gênero, ID do cliente, idade, renda anual e pontuação de gastos. Ele coleta informações dos clientes de dados e do grupo com base em seus comportamentos.
- Baixei o modelo de dados em formato csv.

## Passo-a-passo:
- Entrar no [Azure Portal](https://portal.azure.com) usando as credenciais
- Selecionei **+Create a resource**
- Procurar e selecionar **Azure Machine Learning** e colocar os seguintes ajustes:
    - **Subscription:** *Minha conta do Azure*
    - **Resource group:** *Criei o Projeto1*
    - **Name:** *Escolhi Projeto1-Mall*
    - **Region:** *East US 2*
    - **Storage account:** *Valor default*
    - **Key vault:** *Valor default*
    - **Application insights:** *Valor default* 
    - **Container registry:** *None*

- Selecionei **Review + create** e então selecionei **Create**. Esperei a criação do espeço de trabalho (levou alguns minutos) e então fui para parte de Deployed resource
- Eu selecionei **Launch studio** e loguei no **Azure Machine Learning studio** using my Microsoft account.
- No **Azure Machine Learning studio* , Eu encontrei meu novo espeço de trabalho do meu projeto. 
- No **Azure Machine Learning studio**, Eu selecionei **All workspaces** no menu da esquerda e então selecionei a área de trabalho recém criada.

## Treinamento do Modelo

- No Azure Machine Learning studio, Eu escolhi **Automated ML** page.

- Eu criei um novo Automated ML job com os seguintes ajustes, usando Next quando requerido para prosseguir através da interface de usuário:

Basic settings:

- **Job name:** mslearn-mall-auto
- **New experiment name:** mslearn-mall-shopping
- **Description:** Automated machine learning mall shopping prediction
- **Tags:** none

**Task type & data:**

- **Selected task type:** Regression
- **Selected dataset:** Create a new dataset with the following settings:

**Data type:**

- **Name:** mall-shopping
- **Description:** Historic mall shopping data from data flair website
- **Type:** Tabular

**Data source:**

- Eu escolhi a opção **Select From local files**

- Eu escolhi o arquivo local: Mall_Costumers.csv

- Eu cliquei NEXT

**Settings:**

- **File format:** Delimited
- **Delimiter:** Comma
- **Encoding: UTF-8**
- **Column headers:** Only first file has headers
- **Skip rows:** None
- **Dataset contains multi-line data:** I do not select this option

**Schema:** 

- Eu incluí todas as colunas exceto a "Path"
- Eu revidei os tipos de dados detectados
- Selecionei NEXT
- Selecionei Create. Após o dataset ser criado, selecionei "mall-shopping" para continuar a submeter à Automated ML job.

Task settings:

Task type: Regression
Dataset: mall-shopping
Target column: Spending Score (integer)

**Additional configuration settings:**

- **Primary metric:** Normalized root mean squared error
- **Explain best model:** Unselected
- **Use all supported models:** Unselected. Para restribgir o trabalho a apenas uns poucos algorítimos.
- **Allowed models:** Selecionei somente RandomForest e LightGBM

- **Limits:** Expandi esta seleção

- **Max trials:** 3
- **Max concurrent trials:** 3
- **Max nodes:** 3
- **Metric score threshold:** 0.085 (para que se o modelo atingisse a raiz de erro quadrático metrico de 0.085 ou menos, o trabalho terminasse)
- **Timeout:** 15
- **Iteration timeout:** 15
- **Enable early termination:** Selected

**Validation and test:**

- **Validation type:** Train-validation split
- **Percentage of validation data:** 10
- **Test dataset:** None

**Compute:**

- **Select compute type:** Serverless
- **Virtual machine type:** CPU
- **Virtual machine tier:** Dedicated
- **Virtual machine size:** Standard_DS3_V2*
- **Number of instances:** 1

- Após eu submeti o trabalho de treino e le começou automaticamente.

Esperei 12 minutos para o treino terminar.

# Reviewing the Best Model

Best model Summary

Eu escolhi o Algoritimo: MinMaxScaler, RandomForest

- Selecionei **Metrics**
- **Residuals** e **Predicted_true** - Arquivos estão na pasta figuras

# DEPLOYING e TESTANDO O MODELO

- Na guia de modelo eu escolhi **DEPLOY** e **WEB SERVICE**

**Deploy Model**

- **Name:** predict-sales
- **Description:** Predict cycle sales
- **Compute type:** Azure Container Instance
- **Enable authentication:** Selected

Eu cliquei **DEPLOY** 

## TESTING THE MODEL

No Azure Machine Learning studio, no menu da esquerda, Eu selecionei Endpoints e abri o predict-sales endpoint.

Na pagina do predict-sales endpoint cliquei em Test tab.

Na parte de entrada de dados para testar o painel do endpoint, Eu substitui os valores do template JSON com os seguintes dados de entrada:

```
{
  "Inputs": {
    "data": [
      {
        "CustomerID": 3,
        "Genre": "male",
        "Age": 30,
        "Annual Income (k$)": 130
      }
    ]
  },
  "GlobalParameters": 1.0
}
```

# TEST RESULTS
```
{1 item
"Results":[1 item
0:float51.52
]
}
```


# Machine Learning Project (ENG)

- The first stage was to watch the Dio platform ml course within Bootcamp AI-900
- Learn the concepts of ML and use the Azure platform to test an ML model
- Seek data to carry out the final project of this module
- I used the Flair Data a base for my project [Data Flair Site](https://data-flair.training/blogs/machine-learning-datasets/)
- Among several datasets, I chose the mall customers. -The Mall customers dataset contains information about people visiting the mall. The dataset has gender, customer ID, age, annual income, and spending score. It collects insights from the data and group customers based on their behaviors. Data Link:
- I downloaded the data model in CSV format.

## Step by Step

- Sign into the [Azure portal](https://portal.azure.com) using my Microsoft credentials.
- Select **+ Create a resource**, search for **Machine Learning**, and create a new Azure Machine Learning resource with the following settings:
    - **Subscription:** Your Azure subscription.
    - **Resource group:** *Criei Projeto1*.
    - **Name:** *I choosed Projeto1-mall*
    - **Region:** *East US 2*
    - **Storage account:** *default*
    - **Key vault:** *default*
    - **Application insights:** *default*
    - **Container registry:** *None*

- I Selected **Review + create**, then select **Create**. Wait for your workspace to be created (it took a few minutes), and then I went to the deployed resource.

- Select Launch studio and signed into Azure Machine Learning studio using my Microsoft account.
- In Azure Machine Learning studio, I found my newly created workspace. 
- In Azure Machine Learning studio, I select **All workspaces** in the left-hand menu and then select the workspace you just created.

## Training the Model

- In Azure Machine Learning studio, I Choose **Automated ML** page.

- I Created a new Automated ML job with the following settings, using Next as required to progress through the user interface:

Basic settings:

- **Job name:** mslearn-mall-auto
- **New experiment name:** mslearn-mall-shopping
- **Description:** Automated machine learning mall shopping prediction
- **Tags:** none

**Task type & data:**

- **Selected task type:** Regression
- **Selected dataset:** Create a new dataset with the following settings:

**Data type:**

- **Name:** mall-shopping
- **Description:** Historic mall shopping data from data flair website
- **Type:** Tabular

**Data source:**

- I choose the option **Select From local files**

I selected the local file: Mall_Costumers.csv

I click Next

**Settings:**

- **File format:** Delimited
- **Delimiter:** Comma
- **Encoding: UTF-8**
- **Column headers:** Only first file has headers
- **Skip rows:** None
- **Dataset contains multi-line data:** I do not select this option

**Schema:** 

- I Include all columns other than Path
- I Review the automatically detected types
- I selected NEXT
- Select Create. After the dataset is created, select the mall-shopping dataset to continue to submit the Automated ML job.

Task settings:

Task type: Regression
Dataset: mall-shopping
Target column: Spending Score (integer)

**Additional configuration settings:**

- **Primary metric:** Normalized root mean squared error
- **Explain best model:** Unselected
- **Use all supported models:** Unselected. To restrict the job to try only a few specific algorithms.
- **Allowed models:** Select only RandomForest and LightGBM

- **Limits:** Expand this section
- **Max trials:** 3
- **Max concurrent trials:** 3
- **Max nodes:** 3
- **Metric score threshold:** 0.085 (so that if a model achieves a normalized root mean squared error metric score of 0.085 or less, the job ends.)
- **Timeout:** 15
- **Iteration timeout:** 15
- **Enable early termination:** Selected

**Validation and test:**

- **Validation type:** Train-validation split
- **Percentage of validation data:** 10
- **Test dataset:** None

**Compute:**

- **Select compute type:** Serverless
- **Virtual machine type:** CPU
- **Virtual machine tier:** Dedicated
- **Virtual machine size:** Standard_DS3_V2*
- **Number of instances:** 1

After that I Submit the training job and It started automatically.

I Waited for 12 min job to finish.

# Reviewing the Best Model

Best model Summary

I selected the Algorithm name: MinMaxScaler, RandomForest

- Selected **Metrics**
- **Residuals** and **Predicted_true** - Files on picture folder

# DEPLOYING AND TESTING THE MODEL

- In the model TAB I choose **DEPLOY** and **WEB SERVICE**

**Deploy Model**

- **Name:** predict-sales
- **Description:** Predict cycle sales
- **Compute type:** Azure Container Instance
- **Enable authentication:** Selected

I selected **DEPLOY** 

## TESTING THE MODEL

In Azure Machine Learning studio, on the left hand menu, I select Endpoints and open the predict-sales endpoint.

On the predict-rentals endpoint page view the Test tab.

In the Input data to test endpoint pane, replace the template JSON with the following input data:

```
{
  "Inputs": {
    "data": [
      {
        "CustomerID": 3,
        "Genre": "male",
        "Age": 30,
        "Annual Income (k$)": 130
      }
    ]
  },
  "GlobalParameters": 1.0
}
```

# TEST RESULTS
```
{1 item
"Results":[1 item
0:float51.52
]
}
```
