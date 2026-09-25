# Resumo — Pandas, SQL e Excel

## Objetivo

Reunir os principais conceitos estudados durante a aprendizagem de Python, Pandas, SQL e automação de relatórios em Excel, relacionando os conhecimentos com situações práticas de contabilidade.

---

## 1. Pandas

O Pandas é uma biblioteca Python utilizada para trabalhar com dados estruturados, principalmente através de DataFrames.

### Conceitos estudados

* criação e manipulação de DataFrames;
* filtros;
* criação de novas colunas;
* groupby();
* merge();
* tratamento de valores nulos;
* exportação para Excel.

### Filtros

Para combinar condições em um DataFrame, utilizamos & e colocamos cada condição entre parênteses.

```python
df[
    (df["status"] == "Pendente") &
    (df["valor"] > 5000)
]
```

### Groupby

O groupby() permite agrupar informações e realizar cálculos sobre os grupos.

```python
df.groupby("cliente")["valor"].sum()
```

Também é possível ordenar o resultado:

```python
df.groupby("cliente")["valor"].sum().sort_values(
    ascending=False
)
```

### Merge

O merge() permite cruzar informações entre DataFrames.

```python
df_conciliacao = df_vendas.merge(
    df_banco,
    on="numero_nf",
    how="left"
)
```

O how="left" mantém todos os registros da primeira tabela.

---

## 2. SQL

O SQL foi estudado utilizando DataFrames do Pandas através da biblioteca pandasql.

A função utilizada para executar as consultas foi:

```python
sqldf(consulta)
```

### Principais comandos estudados

```text
SELECT
FROM
WHERE
AND
JOIN
ON
GROUP BY
HAVING
ORDER BY
```

### Funções de agregação

```text
SUM()
COUNT()
AVG()
ROUND()
```

### WHERE x HAVING

WHERE é utilizado para filtrar registros antes do agrupamento.

HAVING é utilizado para filtrar resultados depois do GROUP BY.

---

## 3. LIKE

O operador LIKE permite pesquisar padrões de texto.

```sql
WHERE descricao LIKE %Venda%
```

O símbolo % representa uma quantidade variável de caracteres.

Já:

```sql
NOT LIKE '%Venda%'
```

retorna registros que não correspondem ao padrão.

---

## 4. AS

O AS permite criar um nome para uma coluna calculada.

Exemplo:

```sql
SUM(valor) AS total_valor
```

Isso torna o resultado da consulta mais fácil de interpretar.

---

## 5. Pandas + SQL + Excel

Um dos principais aprendizados foi perceber que as ferramentas podem ser utilizadas em conjunto.

Fluxo estudado:

```text
Dados
  ↓
Pandas
  ↓
SQL
  ↓
Análise e consolidação
  ↓
DataFrame
  ↓
ExcelWriter
  ↓
Arquivo Excel
  ↓
Openpyxl
  ↓
Formatação do relatório
```

### ExcelWriter

O ExcelWriter permite exportar diferentes DataFrames para abas de um mesmo arquivo Excel.

```python
with pd.ExcelWriter("arquivo.xlsx") as writer:
    df_detalhado.to_excel(
        writer,
        sheet_name="Lançamentos_Detalhados",
        index=False
    )

    df_resumo.to_excel(
        writer,
        sheet_name="Resumo_Por_Depto",
        index=False
    )
```

---

## 6. Openpyxl

O openpyxl foi estudado como uma ferramenta complementar para formatar arquivos Excel gerados pelo Pandas.

Conceitos estudados:

* load_workbook()`;
* wb;
* ws;
* Font;
* PatternFill;
* Alignment;
* number_format;
* largura das colunas;
* save().

### Fluxo

```python
wb = openpyxl.load_workbook("arquivo.xlsx")

ws = wb["Lançamentos_Detalhados"]

# alterações de formatação

wb.save("Fechamento_Contabil_Formatado.xlsx")
```

---

## 7. Relação com a contabilidade

Os exercícios foram construídos com situações relacionadas à área contábil e financeira, como:

* notas fiscais;
* impostos;
* vendas;
* recebimentos;
* conciliação bancária;
* lançamentos contábeis;
* centros de custo;
* receitas e despesas;
* fechamento contábil;
* relatórios em Excel.

Essa abordagem permitiu estudar programação e análise de dados utilizando exemplos próximos da área profissional.

---

## 8. Principais aprendizados

O estudo mostrou que Python pode ser utilizado para automatizar tarefas que normalmente seriam realizadas manualmente em planilhas.

Também ficou mais clara a relação entre diferentes ferramentas:

**Python → Pandas → SQL → Excel**

Cada ferramenta pode cumprir uma parte diferente do processo, permitindo construir fluxos de análise e geração de relatórios mais estruturados.
