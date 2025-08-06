# Análise de Regras de Associação de Filmes

Este projeto de Mineração de Dados tem como objetivo analisar um conjunto de dados de avaliações de filmes para identificar padrões de comportamento dos usuários. Utilizando o algoritmo **Apriori**, foi gerado regras de associação que permitem fazer recomendações baseadas no princípio de que "usuários que assistiram ao filme X também tendem assistir ao filme Y".

## 🗂️ Origem dos Dados

Os dados utilizados neste projeto foram obtidos do [Kaggle](https://www.kaggle.com/datasets/parasharmanas/movie-recommendation-system/code?datasetId=3375918), um repositório aberto amplamente utilizado para estudos da área de dados. Foram utilizados os arquivos `ratings.csv` e `movies.csv`, posteriormente adaptados para a análise deste estudo.

## 📜 Sobre o Projeto

O núcleo do projeto consiste em transformar o histórico de avaliações de filmes em um formato transacional, onde cada transação representa os filmes que um usuário avaliou positivamente. A partir disso, foi aplicado o algoritmo Apriori para extrair *itemsets* frequentes e, subsequentemente, gerar regras de associação com métricas de **suporte**, **confiança** e **lift**.

Foi conduzido inicialmente uma análise exploratória dos dados e, em seguida, foi feito experimentos com diferentes valores de suporte mínimo (5%, 10%, 15% e 20%) para analisar o impacto na quantidade e na qualidade das regras geradas.

## 🎯 Objetivos

- Conhecer a estrutura dos dados com EDA.
- Aplicar o algoritmo Apriori para gerar regras de associação entre filmes.
- Avaliar as regras com base em métricas como **confiança**, **suporte** e **lift**.
- Identificar padrões de preferência de usuários para possíveis recomendações.
- Visualizar e interpretar os resultados de forma clara e acessível.

## 📋 Etapas do Projeto

O projeto foi desenvolvido em dois Jupyter Notebooks, cada um focado em uma fase distinta do processo.

#### **Notebook: `exploracao_dados.ipynb`**

1.  **Carregamento e Preparação dos Dados:** Leitura dos arquivos `ratings_alterado.csv` e `movies_alterado.csv` e unificação em um único DataFrame.
2.  **Análise Exploratória de Dados (EDA):** Investigação inicial para entender a distribuição das avaliações, os filmes e gêneros mais populares, e a quantidade de lançamentos por ano.

#### **Notebook: `regras_associacao.ipynb`**

3.  **Pré-processamento para Apriori:**
    * Filtragem do dataset para incluir apenas avaliações consideradas positivas (nota ≥ 4.0).
    * Criação de uma matriz transacional (tabela pivot) onde as linhas representam os usuários e as colunas os filmes.
4.  **Aplicação do Algoritmo Apriori:** Execução do algoritmo com diferentes limiares de suporte mínimo para encontrar conjuntos de filmes frequentemente assistidos juntos.
5.  **Geração e Análise das Regras:** Criação de regras de associação a partir dos *itemsets* frequentes e análise das métricas para identificar as recomendações mais relevantes.

## 🛠️ Tecnologias Utilizadas

* **Python 3.13.5**
* **Pandas:** Para manipulação e análise dos DataFrames.
* **NumPy:** Para operações numéricas.
* **Matplotlib:** Para a visualização dos dados na análise exploratória.
* **Re (Regex):** Para extração do ano de lançamento a partir do título dos filmes.
* **Mlxtend:** Biblioteca utilizada para a implementação do algoritmo Apriori e geração das regras de associação.
* **Jupyter Notebook:** Como ambiente de desenvolvimento e apresentação do projeto.

### Exemplos de Recomendações Geradas (Suporte Mínimo de 15%)

As regras a seguir mostram algumas das associações mais fortes encontradas:

> Usuários que gostaram de **The Lord of the Rings: The Return of the King (2003)**, **The Lord of the Rings: The Two Towers (2002)** também gostaram de **The Lord of the Rings: The Fellowship of the Ring(2001)**, com **93.19%** de confiança.

> Usuários que gostaram de **Star Wars: Episode V - The Empire Strikes Back (1980)**, **Star Wars: Episode VI - Return of the Jedi (1983)** também gostaram de **Star Wars: Episode IV - A New Hope (1977)**, com **89.64%** de confiança.


## 👤 Autor

* **Priscila Borges**
