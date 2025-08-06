# Análise de Regras de Associação para Recomendação de Filmes
### Utilizando o Algoritmo Apriori

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

## 📊 Análise Exploratória (Insights)

A análise inicial revelou insights importantes sobre o dataset:
* **Usuários e Filmes:** O conjunto de dados contém **7.045 usuários** únicos e **62.423 filmes** únicos.
* **Distribuição de Notas:** As notas mais comuns são 4.0 e 5.0, indicando uma tendência dos usuários a avaliar mais os filmes que gostaram.
* **Filmes Mais Populares:** Filmes icônicos como *Forrest Gump*, *Shawshank Redemption* e *Pulp Fiction* estão entre os mais avaliados.
* **Gêneros Predominantes:** Drama, Comédia, Ação e Suspense são os gêneros com maior frequência no dataset.

## ⚙️ Metodologia e Resultados

Para a geração das regras, foi estabelecida a premissa de que uma avaliação com **nota igual ou superior a 4.0** indica que o usuário "gostou" do filme. O algoritmo Apriori foi aplicado com os seguintes valores de suporte mínimo:

| Variações do suporte mínimo | Número de Associações | Estatísticas | Suporte | Confiança | Lift      |
| :--------------------------- | :-------------------- | :----------- | :------ | :-------- | :-------- |
| **Suporte 5%** | 99280                 | min          | 0.05002 | 0.11629   | 1.02899   |
|                              |                       | max          | 0.23320 | 0.97867   | 9.35148   |
|                              |                       | média        | 0.05914 | 0.45297   | 2.91317   |
| **Suporte 10%** | 1202                  | min          | 0.10004 | 0.23389   | 1.21137   |
|                              |                       | max          | 0.23320 | 0.95119   | 4.68967   |
|                              |                       | média        | 0.11916 | 0.51569   | 2.13345   |
| **Suporte 15%** | 98                    | min          | 0.15149 | 0.35910   | 1.21347   |
|                              |                       | max          | 0.23320 | 0.93192   | 4.10476   |
|                              |                       | média        | 0.17689 | 0.59962   | 2.06119   |
| **Suporte 20%** | 12                    | min          | 0.20193 | 0.46944   | 1.43525   |
|                              |                       | max          | 0.23320 | 0.82944   | 2.67250   |
|                              |                       | média        | 0.22147 | 0.61427   | 1.71203   |

Observou-se que, ao aumentar o suporte mínimo, o número de regras geradas diminui drasticamente, mas as regras restantes tendem a ser mais robustas e generalizáveis.

### Exemplos de Recomendações Geradas (Suporte Mínimo de 15%)

As regras a seguir mostram algumas das associações mais fortes encontradas:

> Usuários que gostaram de **The Lord of the Rings: The Return of the King (2003)**, **The Lord of the Rings: The Two Towers (2002)** também gostaram de **The Lord of the Rings: The Fellowship of the Ring(2001)**, com **93.19%** de confiança.

> Usuários que gostaram de **Star Wars: Episode V - The Empire Strikes Back (1980)**, **Star Wars: Episode VI - Return of the Jedi (1983)** também gostaram de **Star Wars: Episode IV - A New Hope (1977)**, com **89.64%** de confiança.


## 👤 Autor

* **Priscila Borges**
