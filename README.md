# Financial Analysis — Microsoft Excel

Projeto de **análise financeira em Microsoft Excel** desenvolvido utilizando dados fictícios da TechBrasil.

O objetivo foi construir uma análise de desempenho financeiro utilizando recursos de Excel aplicados a um cenário empresarial, incluindo comparação **Actual vs Budget**, análise de variações, cruzamento de dados e Tabelas Dinâmicas.

## Objetivo

Analisar dados financeiros da TechBrasil e construir uma estrutura capaz de responder questões como:

- Qual foi a receita realizada em comparação ao orçamento?
- Quais foram as principais variações entre Actual e Budget?
- Como a receita está distribuída entre regiões e produtos?
- Como o OPEX está distribuído entre os centros de custo?
- Quais resultados foram favoráveis ou desfavoráveis em relação ao orçamento?

## Estrutura da Planilha

O arquivo foi organizado em diferentes camadas:

### `01_Dados`

Base principal contendo os registros financeiros utilizados nas análises.

### `02_Cadastros`

Tabela auxiliar contendo informações dos centros de custo, responsáveis e departamentos.

### `03_Analise`

Área destinada aos indicadores financeiros, comparação Actual vs Budget e análise de variações.

### `04_Pivot`

Área contendo Tabelas Dinâmicas e Gráficos Dinâmicos para exploração dos dados.

Essa separação permite manter dados, cadastros, cálculos e análises organizados de forma independente.

## Preparação dos Dados

A base financeira contém informações como:

- Data;
- Conta financeira;
- Centro de custo;
- Região;
- Produto;
- Versão;
- Valor.

Durante a preparação dos dados, os tipos das colunas foram verificados e os valores financeiros foram convertidos para o formato numérico adequado para permitir cálculos e agregações.

## Cruzamento de Dados com PROCX

Foi criada uma tabela auxiliar de centros de custo contendo informações como responsável e departamento.

A função `PROCX` foi utilizada para relacionar os registros financeiros aos respectivos cadastros através do centro de custo.

Exemplo:

```excel
=PROCX([@Cost_Center];tbCentrosCusto[Cost_Center];tbCentrosCusto[Responsavel];"Não encontrado")
```

A lógica é semelhante a um relacionamento entre tabelas utilizando o campo `Cost_Center` como chave.

## Análise Financeira

Os principais indicadores foram calculados utilizando funções como `SOMASES`.

Foram analisados:

- Revenue;
- COGS;
- Personnel;
- Marketing;
- Other OPEX;
- OPEX;
- Resultado Operacional.

A estrutura compara:

- **Actual**;
- **Budget**;
- **Variance**;
- **Variance %**.

### Variance

A variação foi calculada utilizando:

```text
Variance = Actual - Budget
```

e:

```text
Variance % = Variance / Budget
```

A função `SEERRO` foi utilizada para evitar erros em situações nas quais o Budget pudesse ser igual a zero.

## Regras de Negócio

Foram utilizadas funções lógicas para interpretar os resultados como favoráveis ou desfavoráveis.

A análise considera que:

- Receita acima do Budget tende a ser favorável;
- Despesas abaixo do Budget tendem a ser favoráveis;
- Resultado Operacional superior ao Budget tende a ser favorável.

Dessa forma, a classificação não depende apenas do sinal matemático da variação, mas também do significado financeiro do indicador.

## Tabelas Dinâmicas

Foram construídas Tabelas Dinâmicas para analisar os dados sob diferentes perspectivas.

As principais análises incluem:

- Receita Actual vs Budget por região;
- Receita Actual vs Budget por mês;
- Receita Actual vs Budget por produto;
- OPEX por centro de custo.

Também foram utilizados Gráficos Dinâmicos para visualização dos resultados.

## Recursos de Excel Aplicados

Durante o projeto foram utilizados:

- Tabelas do Excel;
- referências estruturadas;
- `PROCX`;
- `SOMASES`;
- `SE`;
- `SEERRO`;
- `OU`;
- Tabelas Dinâmicas;
- Gráficos Dinâmicos;
- filtros;
- segmentação de dados;
- formatação condicional;
- análise Actual vs Budget;
- análise de variação financeira.

## Estrutura do Repositório

```text
excel-financial-analysis/
│
├── README.md
├── TechBrasil_Financial_Analysis.xlsx
│
├── data/
│   └── TechBrasil_Financial_Data_2026.csv
│
└── screenshots/
    ├── financial-analysis.png
    └── pivot-analysis.png
```

## Arquivo do Projeto

A planilha completa está disponível neste repositório:

`TechBrasil_Financial_Analysis.xlsx`

## Observações

A **TechBrasil é uma empresa fictícia** e os dados utilizados foram criados exclusivamente para fins educacionais e de portfólio.
