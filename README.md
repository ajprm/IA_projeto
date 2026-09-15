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

## Descrição do Problema

Fraude em cartão de crédito é um problema que todo banco enfrenta e que custa muito dinheiro por ano, tanto pra instituições financeiras quanto pra quem usa o cartão. A parte complicada desse problema não é só reconhecer o que é uma fraude, mas o fato de que fraudes são muito raras perto do total de transações: no dataset que estamos usando, de 284.807 transações só 492 são fraudulentas. Isso muda a forma como o problema precisa ser tratado, porque um modelo que simplesmente "chutasse" que toda transação é legítima já acertaria mais de 99% das vezes, mesmo sem detectar nenhuma fraude de verdade. A ideia do projeto é usar as técnicas de IA para treinar um modelo que consiga separar transações normais das fraudulentas, usando as colunas do dataset (V1 até V28, que já vêm tratadas por PCA, além do Amount e do Time). Achamos esse problema interessante justamente porque ele junta vários pontos que estamos aprendendo: como lidar com dados desbalanceados, como preparar os dados antes de treinar o modelo, e como avaliar se o modelo é bom sem cair na armadilha de olhar só pra acurácia (que aqui não diz muita coisa sozinha).

## Ética e Responsabilidade no uso da IA

Usar IA pra detectar fraude é útil, mas também traz alguns pontos que valem a pena discutir. O primeiro é a privacidade dos dados. O próprio dataset já foi anonimizado pelos criadores (as variáveis passaram por PCA), o que mostra a preocupação de não expor informação sensível de quem fez as transações. Isso é algo que qualquer projeto que mexe com dados financeiros precisa levar a sério. Outro ponto é o impacto de um modelo errar. Se o modelo classifica uma compra normal como fraude (falso positivo), a pessoa pode ter o cartão bloqueado sem motivo, o que é chato e pode até causar problema em uma emergência. Já se o modelo deixa passar uma fraude de verdade (falso negativo), quem perde é o banco e o cliente. Então tem um equilíbrio meio delicado entre ser rigoroso demais e ser permissivo demais, e isso vai influenciar as escolhas que a gente fizer mais pra frente no projeto. Também tem a questão do desbalanceamento em si: como tem muito pouco exemplo de fraude, existe o risco do modelo aprender de forma tendenciosa ou não generalizar bem pra casos novos. Por isso, mais pra frente vamos precisar tratar isso com cuidado (técnicas tipo SMOTE ou ajuste de peso das classes) e deixar claro no relatório quais são as limitações do que a gente conseguiu fazer. Por fim, um ponto que achamos importante deixar registrado: como esse tipo de sistema afeta diretamente a vida das pessoas (bloquear ou não uma compra), o ideal é que o modelo não seja uma "caixa preta" total, e que dê pra entender minimamente por que ele tomou certa decisão — isso inclusive é algo que a LGPD cobra em situações parecidas. E claro, esse projeto é só acadêmico, então não estamos propondo isso como algo pronto pra ser usado de verdade por um banco, só estudando o problema com as ferramentas que temos até agora.

## Metodologia (resumo)

1. Análise exploratória dos dados (distribuição das classes, correlações, histogramas).
2. Preparação dos dados: normalização de `Amount` e `Time`, divisão treino/teste estratificada e tratamento do desbalanceamento com SMOTE.
3. Treinamento e avaliação de modelos de classificação (Regressão Logística, Random Forest e/ou XGBoost), com foco em métricas adequadas a dados desbalanceados — AUPRC, precisão e recall.

## Aspectos éticos

O dataset utilizado é público e já anonimizado pelos autores originais (variáveis transformadas via PCA), não havendo exposição de dados pessoais identificáveis. A discussão completa sobre os aspectos éticos do uso da IA e a responsabilidade no desenvolvimento da solução está detalhada no relatório do projeto.



