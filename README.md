# 📰 News Intelligence — Pipeline de Ciência de Dados

Plataforma de coleta, processamento e análise de notícias desenvolvida em Python, com visualização interativa em Streamlit e técnicas de Processamento de Linguagem Natural (NLP).

O projeto permite comparar dois portais de notícias, identificar palavras frequentes, analisar sentimentos das manchetes e explorar termos relevantes por meio de TF-IDF.

## 🎯 Objetivo do projeto

Desenvolver um pipeline de Ciência de Dados capaz de transformar notícias disponíveis na web em dados estruturados, aplicando técnicas de processamento textual e análise exploratória para gerar informações úteis sobre o conteúdo publicado.

## ✨ Funcionalidades

- **Coleta de notícias:** extração de manchetes e metadados utilizando Requests e BeautifulSoup.
- **Processamento de dados:** normalização de textos, padronização de campos e tratamento de registros duplicados.
- **Armazenamento de dados:** exportação de dados brutos e processados em arquivos JSON.
- **Análise exploratória:** cálculo de métricas gerais sobre as notícias coletadas.
- **Frequência de palavras:** identificação e classificação dos termos mais recorrentes nas manchetes.
- **Análise de sentimentos:** classificação das manchetes em positivas, negativas ou neutras utilizando um modelo pré-treinado de NLP.
- **TF-IDF:** identificação de termos relevantes nos conjuntos de manchetes.
- **Dashboard interativo:** visualização dos resultados e comparação entre dois portais de notícias com Streamlit.
- **Visualização individual:** consulta das manchetes, classificação de sentimento e links para as notícias originais.

## 🛠️ Tecnologias utilizadas

| Tecnologia | Aplicação |
|---|---|
| Python | Desenvolvimento e integração do pipeline |
| Requests | Requisições HTTP para coleta de dados |
| BeautifulSoup | Extração e análise de conteúdo HTML |
| Pandas | Organização e manipulação de dados tabulares |
| Scikit-learn | Vetorização textual e cálculo de TF-IDF |
| Transformers | Utilização de modelo pré-treinado para análise de sentimentos |
| PyTorch | Execução do modelo de NLP |
| Streamlit | Construção do dashboard interativo |
| JSON | Armazenamento de dados brutos e processados |

## 📂 Estrutura do projeto

```text
news-intelligence-pipeline_Projeto_Ciência_de_Dados/
│
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
│
├── src/
│   ├── __init__.py
│   ├── coleta.py
│   ├── processamento.py
│   ├── sentimento.py
│   ├── analise.py
│   └── armazenamento.py
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── exports/
│
└── tests/
```

**Responsabilidade dos principais módulos:**

- `app.py`: interface do usuário e integração das análises.
- `src/coleta.py`: coleta de notícias e extração de metadados.
- `src/processamento.py`: limpeza, normalização, remoção de duplicatas, frequência de palavras e TF-IDF.
- `src/sentimento.py`: classificação de sentimentos das manchetes e cálculo do sentimento predominante.
- `src/analise.py`: cálculo de métricas gerais.
- `src/armazenamento.py`: gravação dos dados coletados em arquivos JSON.
- `data/raw/`: armazenamento dos dados brutos.
- `data/processed/`: armazenamento dos dados normalizados e processados.
- `data/exports/`: diretório destinado a futuras exportações.

## ⚙️ Instalação e configuração

### 1. Pré-requisitos

- Python instalado.
- Git instalado, caso deseje clonar o repositório.
- Conexão com a internet para coletar notícias e baixar o modelo de sentimentos na primeira execução.

### 2. Clone o repositório

```bash
git clone URL_DO_SEU_REPOSITORIO
cd news-intelligence-pipeline_Projeto_Ciência_de_Dados
```

Substitua `URL_DO_SEU_REPOSITORIO` pelo endereço real do seu repositório no GitHub.

### 3. Crie um ambiente virtual

No Windows, utilizando PowerShell:

```powershell
python -m venv venv
```

Ative o ambiente virtual:

```powershell
.\venv\Scripts\Activate.ps1
```

### 4. Instale as dependências

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 5. Execute a aplicação

Na raiz do projeto, com o ambiente virtual ativado:

```powershell
streamlit run app.py
```

O Streamlit disponibilizará o endereço local da aplicação no terminal.

## 🚀 Como utilizar

1. Acesse a aplicação pelo navegador.
2. Informe as URLs de dois portais de notícias.
3. Clique em **Analisar portais**.
4. Explore as métricas, a frequência de palavras, o TF-IDF e as classificações de sentimento.
5. Consulte as manchetes coletadas e acesse os links das notícias originais.
6. Se desejar persistir os resultados da coleta, utilize a opção de extração e salvamento de dados disponibilizada ao final da análise.

## 🧠 Análise de sentimentos

O projeto utiliza o modelo pré-treinado:

`lxyuan/distilbert-base-multilingual-cased-sentiments-student`

As manchetes são classificadas em três categorias:

- 😊 Positivo
- 😐 Neutro
- 😡 Negativo

A aplicação também apresenta a pontuação de confiança atribuída pelo modelo para cada classificação e calcula o sentimento predominante do conjunto analisado.

As classificações são estimativas automatizadas e podem apresentar erros, especialmente em manchetes com ironia, ambiguidades ou contextos que exigem interpretação mais aprofundada.

## 📊 Análise textual

O projeto utiliza duas abordagens complementares:

**Frequência de palavras:** contabiliza os termos recorrentes nas manchetes após a normalização e a remoção de palavras comuns (*stopwords*).

**TF-IDF (Term Frequency–Inverse Document Frequency):** calcula a relevância relativa dos termos considerando sua ocorrência nos documentos analisados.

Essas técnicas permitem explorar os principais assuntos presentes nas manchetes e observar diferenças entre os portais selecionados.

## 💾 Armazenamento de dados

Os dados podem ser salvos em arquivos JSON, organizados em duas etapas:

- `data/raw/`: registros originais obtidos na coleta.
- `data/processed/`: registros normalizados e tratados, acompanhados de estatísticas do processamento.

O armazenamento é opcional durante a utilização do dashboard, permitindo analisar os dados sem exigir que cada execução gere arquivos permanentes.

## ⚠️ Limitações conhecidas

- A quantidade e a qualidade das notícias coletadas dependem da estrutura HTML e das condições de acesso de cada portal.
- Alterações no site de origem podem exigir ajustes nos seletores utilizados na extração.
- A análise de sentimentos é realizada sobre manchetes e não representa necessariamente o sentimento do artigo completo.
- Os resultados de TF-IDF e frequência refletem o conjunto de notícias coletadas naquele momento.
- O projeto depende de conexão com a internet para realizar novas coletas e, quando necessário, baixar o modelo pré-treinado.

## 🔮 Possíveis melhorias futuras

- Implementação de testes automatizados.
- Expansão das métricas de qualidade da coleta.
- Comparação histórica entre diferentes coletas.
- Exportação dos resultados em CSV e Excel.
- Evolução das visualizações e dos indicadores do dashboard.
- Aprimoramento da robustez da coleta para diferentes portais.

## 👨‍💻 Sobre o projeto

Projeto acadêmico e prático desenvolvido para aplicar conceitos de Ciência de Dados, Python, processamento textual, análise exploratória e Processamento de Linguagem Natural.

O desenvolvimento busca consolidar conhecimentos em coleta, tratamento, análise e visualização de dados por meio de uma aplicação funcional e modular.

---

**Tecnologias principais:** Python · Pandas · Scikit-learn · Transformers · PyTorch · Streamlit

**Área:** Ciência de Dados | NLP | Análise de Dados
