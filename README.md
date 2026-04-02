# Classificação de Vagas por Nível (Junior vs Senior)

Projeto de **Machine Learning** desenvolvido em **Python** para classificar vagas de emprego como **Junior** ou **Senior** com base nas **skills exigidas** em cada oportunidade.

O modelo utiliza **TF-IDF** para representar as habilidades em formato numérico e **Regressão Logística** para prever o nível da vaga, além de identificar quais skills mais influenciam cada classe.

---

# Sobre o Projeto

Este projeto foi construído a partir de dois arquivos de dados:

- `job_postings.csv`
- `job_skills.csv`

Os datasets são integrados pela coluna **`job_link`**, permitindo relacionar cada vaga às respectivas habilidades exigidas.

Após a integração dos dados, o pipeline realiza:

- filtragem dos níveis de interesse
- transformação textual das skills
- vetorização com **TF-IDF**
- treinamento de um classificador binário
- avaliação do desempenho
- interpretação dos coeficientes do modelo

A proposta é prever se uma vaga pertence ao nível **Junior** ou **Senior** com base apenas no conjunto de skills associado à vaga.

---

# Objetivo

Criar um modelo de classificação binária capaz de:

- prever o nível da vaga com base nas skills descritas
- diferenciar vagas **Junior** e **Senior**
- avaliar o desempenho do modelo
- interpretar quais habilidades mais impactam a classificação final

---

# Base de Dados

O projeto utiliza os seguintes arquivos:

- `job_postings.csv` → informações gerais das vagas
- `job_skills.csv` → skills associadas a cada vaga

A integração é feita por:

- `job_link`

---

# Estrutura do Notebook

O notebook `classificador.ipynb` executa um fluxo único com as seguintes etapas:

## 1. Importação das bibliotecas
Carregamento de bibliotecas para manipulação de dados, vetorização de texto, treinamento e avaliação do modelo.

## 2. Carregamento dos dados
Leitura dos arquivos CSV e verificação do formato inicial dos datasets.

## 3. Merge e limpeza
União entre `job_postings` e `job_skills` por `job_link`, seguida da remoção de registros nulos em:

- `job_skills`
- `job_level`

## 4. Criação da variável alvo
O projeto trabalha apenas com duas categorias:

- `Associate` → **Junior (0)**
- `Mid senior` → **Senior (1)**

## 5. Pré-processamento das skills
As skills são separadas, limpas e transformadas em texto contínuo, substituindo espaços por underline para preservar termos compostos.

## 6. Vetorização com TF-IDF
As skills processadas são convertidas em matriz numérica com:

- `min_df=10`
- `max_df=0.9`

## 7. Separação entre treino e teste
Os dados são divididos em:

- **80% para treino**
- **20% para teste**

com `random_state=42` e `stratify=y`.

## 8. Treinamento do modelo
O classificador utilizado é:

- **LogisticRegression**
- `max_iter=1000`
- `class_weight="balanced"`

## 9. Avaliação
O notebook calcula:

- acurácia
- relatório de classificação
- matriz de confusão

## 10. Interpretação
Por fim, o projeto identifica as skills com maior influência positiva para:

- vagas **Senior**
- vagas **Junior**

---

# Tecnologias Utilizadas

- **Python**
- **Pandas**
- **NumPy**
- **Scikit-learn**
- **Jupyter Notebook**

---

# Bibliotecas Aplicadas

As principais bibliotecas utilizadas são:

- `pandas`
- `numpy`
- `sklearn.model_selection`
- `sklearn.feature_extraction.text`
- `sklearn.linear_model`
- `sklearn.metrics`

---

# Resumo dos Dados

Após a execução do pipeline, o projeto trabalha com os seguintes volumes:

- `job_postings.csv` → **12.217 linhas**
- `job_skills.csv` → **12.217 linhas**
- após o merge e limpeza → **12.212 registros**
- matriz TF-IDF final → **12.212 vagas x 3.392 skills**

Distribuição da variável alvo:

- **Junior (0)** → 1.297 vagas
- **Senior (1)** → 10.915 vagas

Divisão dos dados:

- **Treino** → 9.769 vagas
- **Teste** → 2.443 vagas

---

# Desempenho do Modelo

Na execução atual do notebook, o modelo obteve:

- **Acurácia geral:** `0.7990`

## Matriz de Confusão

```text
                 Pred: Junior   Pred: Senior
Real: Junior            152            107
Real: Senior            384           1800
```

Esse resultado mostra que o modelo tem bom desempenho geral, mas também evidencia um conjunto de classes desbalanceado, com predominância de vagas Senior.

---

# Skills Mais Relevantes

## Skills que mais aumentam a probabilidade de Senior

- `b_testing`
- `data_preparation`
- `google_cloud`
- `construction_management`
- `medical_technology`
- `ml`
- `clinical_research`
- `statistical_techniques`
- `collaboration`
- `airflow`

## Skills que mais aumentam a probabilidade de Junior

- `volunteerism`
- `data_entry`
- `inventory_management`
- `active_directory`
- `data_products`
- `virtual_assistants`
- `sagemaker`
- `data_representation`
- `commercial_acumen`
- `data_collection`

---

# Como Executar

## Pré-requisitos

Antes de executar o projeto, tenha instalado:

- Python 3.x
- pip
- Jupyter Notebook ou JupyterLab

Também é necessário manter os arquivos abaixo na mesma pasta do notebook:

- `classificador.ipynb`
- `job_postings.csv`
- `job_skills.csv`

## Instalação das Dependências

```bash
pip install pandas numpy scikit-learn notebook
```

## Execução

Abra o notebook e execute as células:

```bash
jupyter notebook
```

ou

```bash
jupyter lab
```

Depois, abra o arquivo:

```text
classificador.ipynb
```

---

# Estrutura Esperada dos Arquivos

```text
projeto/
├── classificador.ipynb
├── job_postings.csv
├── job_skills.csv
└── README.md
```

---

# Aplicações do Projeto

Esse tipo de solução pode ser útil em cenários como:

- análise de vagas de emprego
- apoio à triagem de oportunidades
- estudos sobre senioridade e habilidades
- mineração de dados de mercado de trabalho
- projetos acadêmicos de classificação textual

---

# Possíveis Melhorias Futuras

O projeto pode ser expandido com melhorias como:

- teste com outros algoritmos de classificação
- ajuste de hiperparâmetros
- uso de embeddings em vez de TF-IDF
- inclusão de mais níveis de senioridade
- balanceamento mais sofisticado entre classes
- visualizações gráficas dos resultados
- interface para prever novas vagas manualmente

---

# Licença

Projeto desenvolvido para fins acadêmicos, estudo de Machine Learning e análise de classificação de vagas.
