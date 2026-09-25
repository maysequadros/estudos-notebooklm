# Exercício — Consultas SQL Básicas com Pandas

## Objetivo

Praticar a utilização da linguagem SQL sobre DataFrames do Pandas utilizando a biblioteca pandasql.

## O que precisava ser feito

### Consulta 1 — Filtro com WHERE

Selecionar somente os lançamentos classificados como "Despesa" e com valor superior a R$ 2.000,00.

```sql
SELECT *
FROM df_lancamentos
WHERE tipo = 'Despesa'
AND valor > 2000;
```

### Consulta 2 — JOIN

Relacionar os lançamentos aos respectivos centros de custo utilizando a coluna "id_centro_custo".

```sql
SELECT
    id_lancamento,
    descricao,
    tipo,
    valor,
    nome_departamento
FROM df_lancamentos
JOIN df_centros
ON df_lancamentos.id_centro_custo = df_centros.id_centro_custo;
```

### Consulta 3 — GROUP BY e SUM

Agrupar os lançamentos por departamento e tipo, calcular o valor total e ordenar do maior para o menor.

```sql
SELECT
    nome_departamento,
    tipo,
    SUM(valor) AS total_valor
FROM df_lancamentos
JOIN df_centros
ON df_lancamentos.id_centro_custo = df_centros.id_centro_custo
GROUP BY nome_departamento, tipo
ORDER BY SUM(valor) DESC;
```

## Principais conceitos praticados

* SELECT
* FROM
* WHERE
* AND
* JOIN
* ON
* GROUP BY
* SUM()
* ORDER BY
* AS
* sqldf()

## Dificuldades encontradas

Durante os exercícios, foi necessário compreender como a lógica utilizada no Pandas pode ser representada utilizando SQL.

Também foi necessário entender que o JOIN precisa indicar a relação entre as tabelas por meio da cláusula ON.

Outro aprendizado foi o uso do AS para dar um nome mais claro a uma coluna calculada, como o resultado de SUM(valor).

## O que aprendi

Aprendi que SQL permite consultar e transformar dados utilizando uma estrutura diferente da utilizada diretamente no Pandas.

Também comecei a perceber a relação entre os conceitos:

| Pandas          | SQL        |
| --------------- | ---------- |
| Filtro          | WHERE    |
| merge()       | JOIN     |
| groupby()     | GROUP BY |
| sum()         | SUM()    |
| sort_values() | ORDER BY |

## Aplicação na contabilidade

Esses comandos podem ser utilizados para consultar lançamentos contábeis, analisar despesas e receitas, relacionar lançamentos aos centros de custo e gerar informações para relatórios financeiros.
