# DataView PY — Exploração e Análise de Dados de E-commerce

## Sobre o projeto

O **DataView PY** é um projeto de análise exploratória de dados (EDA) desenvolvido em Python como parte do Mini-Projeto Avaliativo do Módulo 1 do curso *Desenvolvedor(a) em IA para Análise Preditiva*. O notebook lê, limpa, transforma, analisa e visualiza um dataset sintético de vendas de e-commerce brasileiro, gerando métricas e insights relevantes para uma reunião de diretoria.

---

## O que o projeto analisa

- Receita total e volume de pedidos por mês e trimestre
- Top 5 produtos e categorias por receita
- Desempenho de vendas por região e estado
- Segmentação de clientes por nível de gasto (Bronze, Prata, Ouro)
- Comparação entre dados com e sem tratamento de outliers (v1 e v2)
- Receita por forma de pagamento (Pix, Boleto, Cartão de Crédito, Cartão de Débito)
- Exportação de relatórios em CSV e JSON

---

## Objetivo

Praticar os principais conceitos de Python e análise de dados:

- Lógica de programação com Python
- Variáveis, tipos de dados e operadores (int, float, str, bool, list, dict)
- Condicionais (if, elif, else) e repetição (for, while)
- Funções com parâmetros, retorno e funções lambda
- Funções reutilizáveis e funções de ordem superior (callback)
- Leitura e escrita de arquivos CSV e JSON
- Módulo `datetime` para manipulação de datas
- Expressões regulares com o módulo `re`
- Pandas: DataFrames, limpeza, groupby, filtros e transformações
- NumPy: arrays, operações vetorizadas, broadcasting e boolean indexing
- Detecção e tratamento de outliers com IQR
- Matplotlib e Seaborn: gráficos, customização e exportação em PNG
- Versionamento com GitHub

---

## Dataset

O projeto utiliza um dataset **sintético de e-commerce brasileiro** gerado diretamente no código (RF01), com 300 registros e as seguintes colunas:

| Coluna | Descrição |
|---|---|
| `id_pedido` | Identificador único do pedido |
| `data_pedido` | Data do pedido (formato YYYY-MM-DD) |
| `cliente` | Identificador do cliente |
| `produto` | Nome do produto vendido |
| `categoria` | Categoria do produto (Eletrônicos, Vestuário, etc.) |
| `regiao` | Região do Brasil |
| `estado` | Estado da federação |
| `quantidade` | Quantidade de itens no pedido |
| `preco_unitario` | Preço unitário do produto (R$) |
| `forma_pagamento` | Método de pagamento utilizado |

O dataset contém dados **intencionalmente sujos** para praticar limpeza: valores nulos, datas inválidas e strings com espaços extras.

---

## Versão escolhida para data/final/

Foi escolhida a versão **v2 (outliers removidos)** como base para a análise final, pois garante que as métricas agregadas e as visualizações reflitam o comportamento típico das vendas, sem distorção por valores extremos. A v1 (com outliers) está preservada em `data/processed/v1_com_outliers/` para consulta futura.

---

## Como executar

### No Google Colab (recomendado)

1. Faça upload da pasta `notebooks/` ou apenas do arquivo `dataview.ipynb`
2. Abra o arquivo no Colab
3. Execute as células na ordem, de cima para baixo (`Runtime > Run All`)
4. Os arquivos de saída serão gerados nas pastas relativas ao notebook

### Localmente com VS Code

1. Instale o Python 3.10+ em [python.org](https://python.org) (marque "Add to PATH")
2. Instale o VS Code em [code.visualstudio.com](https://code.visualstudio.com)
3. Instale as extensões **Python** e **Jupyter** (Microsoft) no VS Code
4. Clone ou baixe o repositório
5. Abra a pasta do projeto no VS Code
6. No terminal, crie e ative o ambiente virtual:

```bash
# Criar ambiente virtual
python -m venv .venv

# Ativar (Windows PowerShell)
.venv\Scripts\activate

# Ativar (Mac/Linux)
source .venv/bin/activate
```

7. Instale as dependências:

```bash
pip install pandas numpy matplotlib seaborn notebook ipykernel
```

8. Abra o arquivo `notebooks/dataview.ipynb` no VS Code
9. Selecione o kernel `.venv` no canto superior direito
10. Execute as células com `Shift+Enter` na ordem

---

## Estrutura do projeto

```
dataview_py/
├── data/
│   ├── raw/                          # Dataset bruto gerado no código
│   │   └── vendas.csv
│   ├── processed/
│   │   ├── v1_com_outliers/          # Dados limpos, outliers mantidos
│   │   │   └── vendas_v1.csv
│   │   └── v2_outliers_tratado/      # Dados limpos, outliers removidos (IQR)
│   │       └── vendas_v2.csv
│   └── final/                        # Dataset final usado na análise
│       └── vendas_final.csv
├── notebooks/
│   └── dataview.ipynb                # Notebook principal de EDA
├── outputs/
│   ├── metricas_por_mes.csv          # Métricas mensais agregadas
│   ├── segmentacao_clientes.csv      # Classificação Bronze/Prata/Ouro
│   ├── estatisticas_gerais.json      # Estatísticas NumPy exportadas
│   └── graficos/
│       ├── receita_por_mes.png       # Gráfico de linha — receita mensal
│       ├── top_produtos.png          # Gráfico de barras — top 5 produtos
│       ├── dist_regiao.png           # Boxplot — receita por região
│       └── receita_por_pagamento.png # Barras — receita por forma de pagamento
└── README.md
```

---

## Requisitos funcionais implementados

| RF | Descrição |
|---|---|
| RF01 | Geração do dataset sintético de e-commerce com dados sujos |
| RF02 | Inspeção inicial com `.shape`, `.dtypes`, `.isnull()` e `.describe()` |
| RF03 | Limpeza: regex para strings, conversão de datas, remoção de nulos |
| RF04 | Detecção e tratamento de outliers por IQR — versões v1 e v2 |
| RF05 | Colunas derivadas: `receita_total`, `mes`, `trimestre`, `ano`, `faixa_receita_item` |
| RF06 | Métricas agregadas com `groupby` por mês, produto, categoria, região e estado |
| RF07 | Segmentação de clientes com `lambda` — Bronze, Prata e Ouro |
| RF08 | Estatísticas com NumPy: vetorização, broadcasting e boolean indexing |
| RF09 | 4 gráficos exportados em PNG com Matplotlib e Seaborn |
| RF10 | Funções de ordem superior com callback e 2 usos de `lambda` |
| RF11 | Exportação de CSV com `to_csv()` e JSON com `json.dump()` / `json.load()` |
| RF12 | Consolidação final e verificação de todos os arquivos gerados |

---

## Ferramentas utilizadas:

- Python 3.10+
- VS Code com extensões Python e Jupyter
- Bibliotecas: `pandas`, `numpy`, `matplotlib`, `seaborn`, `re`, `datetime`, `os`, `json`, `random`
- GitHub para versionamento


## Pontos a melhorar. Identifico três pontos de melhoria para versões futuras do projeto:
** Primeiro, aplicar modelos de Machine Learning sobre o dataset final — como regressão para prever receita dos próximos meses.
** Segundo, criar um dashboard interativo com bibliotecas como Plotly ou Streamlit, permitindo filtrar os dados por região, categoria e período.
**E terceiro, automatizar o pipeline de dados para que novas entradas de vendas sejam processadas e analisadas automaticamente, sem intervenção manual."
---

## Vídeo de demonstração:

[Inserir link do Google Drive ou YouTube aqui]

---

## Repositório

[(https://github.com/lindomarandradegertrudes/Miniprojeto_Lindomar_WEEK8)]

---

## Autor

**Lindomar Andrade Gertrudes**  
Curso: Desenvolvedor(a) em IA para Análise Preditiva — Módulo 1  
Mini-Projeto Avaliativo — Semana 08
