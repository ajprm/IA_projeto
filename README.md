# Detecção de Fraude em Transações de Cartão de Crédito

Projeto da disciplina **Inteligência Artificial – 7ºJ SI - Noite**, ministrada pelo Prof. Dr. Leandro Zerbinatti, no curso de Sistemas de Informação da Universidade Presbiteriana Mackenzie.

## Alunas e RA

| Nome | RA 
|---|---
| Anna Julia Santos de Paula | 10420681
| Eduarda Dantas Azevedo Silva | 10419951
| Sara de Oliveira Silva Omena | 10425441
## Sobre o projeto

O objetivo deste projeto é aplicar técnicas de Inteligência Artificial (Machine Learning) na detecção de fraudes em transações de cartão de crédito, utilizando o framework **scikit-learn** (Opção Framework).

Trata-se de um problema de classificação binária fortemente desbalanceado: a grande maioria das transações é legítima, e apenas uma pequena fração corresponde a fraudes — o que exige cuidados específicos na preparação dos dados e na escolha das métricas de avaliação.

## Dataset

- **Nome:** Credit Card Fraud Detection
- **Fonte:** [Kaggle — mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- **Conteúdo:** 284.807 transações de cartão de crédito realizadas por titulares europeus em setembro de 2013, das quais 492 (0,172%) são fraudulentas.
- **Variáveis:** `V1` a `V28` (componentes resultantes de uma transformação PCA aplicada pelos autores originais por motivos de confidencialidade), `Time`, `Amount` e `Class` (0 = transação normal, 1 = fraude).

> O dataset não está incluído neste repositório por seu tamanho — baixe-o diretamente no link acima e coloque o arquivo `creditcard.csv` na pasta `dataset/`.

## Estrutura do repositório

```
├── README.md
├── relatorio/
│   └── relatorio_projeto.pdf        # Relatório do projeto (template da disciplina)
├── dataset/
│   └── creditcard.csv               # Dataset (baixar do Kaggle — não versionado)
└── notebooks/
    ├── preparacao_dados.ipynb       # Preparação dos dados (Anna Julia)
    ├── analise_exploratoria_1.ipynb # Análise exploratória — parte 1 (Eduarda)
    └── analise_exploratoria_2.ipynb # Análise exploratória — parte 2 (Sara)
```

## Como executar

1. Clone o repositório.
2. Baixe o `creditcard.csv` no [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) e salve em `dataset/`.
3. Instale as dependências:
   ```
   pip install pandas numpy scikit-learn imbalanced-learn matplotlib
   ```
4. Execute os notebooks na pasta `notebooks/`, na ordem indicada acima.

## Metodologia (resumo)

1. Análise exploratória dos dados (distribuição das classes, correlações, histogramas).
2. Preparação dos dados: normalização de `Amount` e `Time`, divisão treino/teste estratificada e tratamento do desbalanceamento com SMOTE.
3. Treinamento e avaliação de modelos de classificação (Regressão Logística, Random Forest e/ou XGBoost), com foco em métricas adequadas a dados desbalanceados — AUPRC, precisão e recall.

## Aspectos éticos

O dataset utilizado é público e já anonimizado pelos autores originais (variáveis transformadas via PCA), não havendo exposição de dados pessoais identificáveis. A discussão completa sobre os aspectos éticos do uso da IA e a responsabilidade no desenvolvimento da solução está detalhada no relatório do projeto.
