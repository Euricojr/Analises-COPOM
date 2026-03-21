# 🏛️ Análise das Atas do COPOM

Este projeto automatiza a análise das atas do Comitê de Política Monetária (COPOM) do Banco Central do Brasil. Ele foi migrado de um ambiente Google Colab para uma estrutura local profissional, permitindo o uso de ferramentas de análise de dados e processamento de linguagem natural (NLP).

## 📊 O que o projeto faz?

- **Mineração de Dados**: Extração de texto de PDFs das atas do COPOM.
- **Processamento de Linguagem Natural (NLP)**: Uso de ferramentas como `nltk` e `pdfplumber`.
- **Visualização**: Geração de nuvens de palavras (`wordcloud`) e gráficos com `matplotlib`.
- **Análise Estatística**: Aplicação de modelos com `scikit-learn`.

## 🛠️ Configuração do Ambiente Local

Para rodar este projeto na sua máquina, siga os passos abaixo:

### 1. Criar e Ativar Ambiente Virtual
O projeto já conta com um `.venv`. O VS Code deve detectá-lo automaticamente ao abrir o notebook.

### 2. Instalação de Dependências
Ao abrir o notebook `Analises_atas_copom.ipynb`, execute a primeira célula que contém o comando:
```python
%pip install requests pandas pdfplumber nltk wordcloud matplotlib scikit-learn
```

### 3. Principais Bibliotecas Utilizadas
| Biblioteca | Função |
| :--- | :--- |
| `pandas` | Manipulação de dados estruturados |
| `pdfplumber` | Extração precisa de texto de arquivos PDF |
| `nltk` | Processamento de linguagem natural (tokens, stopwords) |
| `wordcloud` | Criação de visualizações de frequência de palavras |
| `matplotlib` | Plotagem de gráficos e visualizações |
| `scikit-learn` | Modelagem e análise de dados |

## 🚀 Status do Projeto

- [x] Correção de erros de sintaxe e inicialização do arquivo `.ipynb`.
- [x] Migração dos comandos de instalação do ambiente Colab para local.
- [x] Estruturação da primeira célula de análise.

---
*Projeto desenvolvido para fins de análise macroeconômica e automação de processamento de documentos oficiais.*