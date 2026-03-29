# 🏛️ Monitor de Sentimento do COPOM via NLP

Este projeto automatiza a coleta, o processamento e a análise das atas do Comitê de Política Monetária (COPOM) do Banco Central do Brasil. O objetivo principal é extrair insights fundamentais do texto oficial do Banco Central, transformando atas difíceis de digerir (em formato PDF) em indicadores quantitativos de política monetária, incerteza e sentimento de mercado (*Hawkish* vs *Dovish*).

## 📊 O que o projeto faz?

Em vez de apenas ler os PDFs, o notebook (`Analises_atas_copom.ipynb`) realiza uma trilha de inteligência de dados dividida em 5 níveis:

### 1. Extração Automatizada (Scraping)
Utiliza a API oficial do site do Banco Central para mapear os PDFs das atas mais recentes. Através da biblioteca `pdfplumber`, o texto é extraído das páginas e consolidado em um *Corpus* de pesquisa em um DataFrame do Pandas.

### 2. Nível 1: Análise Visual (Nuvem de Palavras)
Aplica técnicas básicas de NLP para visualizar a frequência de termos. Remove *stopwords* (preposições, artigos e palavras técnicas rotineiras que não agregam valor) e sinaliza visualmente a predominância temática de cada reunião com a ajuda do `wordcloud`.

### 3. Nível 2: Monitor de Sentimento e Sinalização (Hawkish vs Dovish)
O "Duelo de Narrativas". Classifica o discurso e mede o tom da autoridade monetária:
- **Hawkish:** Foco em combater a inflação e possível alta de juros (termos como "cautela", "preocupação", "piora").
- **Dovish:** Foco em estimular a economia e possível queda de juros (termos como "desaceleração", "otimismo", "abrandamento").
- O cálculo gera Scores relativos e o **Sentimento Líquido** das atas, indicando para onde o Banco Central está pendendo.

### 4. Nível 3: O Índice de Incerteza (Fuzziness Ratio)
Mede o grau de incerteza expresso nas atas. Utilizando como base um dicionário quantitativo de incertezas de mercado (inspirado no *Loughran-McDonald* e traduzido para o português), avalia menções de dúvidas financeiras, indefinições e volatilidade, construindo um gráfico temporal da incerteza do Comitê.

### 5. Nível 4: TF-IDF & Clustering (O que mudou de fato?)
Identifica especificamente o que a ata traz de *novo* em relação a todas as reuniões anteriores. Utiliza o modelo `TF-IDF` do `scikit-learn` para puxar os termos exclusivos de cada reunião e extrair as temáticas únicas discutidas no momento. O dashboard final agrupa esses *insights* usando `Jinja2`.

---

## 🛠️ Configuração do Ambiente Local

Para rodar este projeto e gerar o seu próprio monitor de sentimento, siga os passos abaixo:

### 1. Criar e Ativar Ambiente Virtual (Recomendado)
Para garantir bom funcionamento das bibliotecas de ML e NLP, inicie seu projeto em uma `.venv`.

### 2. Instalação de Dependências
O próprio notebook verifica e instala os pacotes na primeira célula. Se preferir rodar no terminal, utilize:
```bash
pip install requests pandas pdfplumber nltk wordcloud matplotlib scikit-learn jinja2
```

### 3. Principais Bibliotecas Utilizadas
| Biblioteca | Função |
| :--- | :--- |
| `requests` | Consumo da API BCB e download de ativos em memória |
| `pandas` | Manipulação e criação de dicionários e DataFrames |
| `pdfplumber` | Extração ágil e fiel do texto das Atas em formato PDF |
| `nltk` | Biblioteca padrão ouro de NLP (opera *tokens* e *stopwords*) |
| `wordcloud` | Criação visual das nuvens de palavras e *insights* gráficos |
| `matplotlib` | Plotagem de gráficos sobre a incerteza e sentimento líquido |
| `scikit-learn` | Modelagem matemática de texto (`TfidfVectorizer`) |
| `jinja2` | Estilização HTML para o output dos DataFrames (Dashboard Final) |

---
*Projeto desenvolvido para revolucionar o processamento de diretrizes monetárias, transformando o extenso "Economês" em métricas mensuráveis.*