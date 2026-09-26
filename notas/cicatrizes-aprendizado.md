# Cicatrizes e Aprendizados

Durante o desenvolvimento dos estudos e exercícios, alguns erros e dificuldades ajudaram a compreender melhor os conceitos. Esses registros fazem parte do processo de aprendizagem ativa.

## 1. Cálculos tributários com Python

### Dificuldade

Ao calcular os impostos, tive dúvidas sobre como percorrer as linhas do DataFrame e armazenar os resultados.

### O que aprendi

Aprendi a utilizar iterrows() para percorrer as linhas de um DataFrame e entendi que o resultado do cálculo precisa ser armazenado para depois criar uma nova coluna.

Também aprendi que linha é apenas o nome de uma variável e representa a linha que está sendo analisada.

---

## 2. Decimal em Python

### Erro

Inicialmente utilizei 0,06 para representar 6%.

### O que aprendi

Em Python, números decimais utilizam ponto:

```python
0.06
```

e não vírgula.

Esse erro ajudou a entender uma diferença importante entre a escrita de números no português e a sintaxe utilizada na programação.

---

## 3. `=` e `==`

### Dificuldade

Tive dúvidas sobre a diferença entre atribuição e comparação.

### O que aprendi

```python
=
```

é utilizado para atribuir um valor.

```python
==
```

é utilizado para comparar valores.

Essa diferença passou a fazer mais sentido depois dos exercícios de filtragem de DataFrames.

---

## 4. Filtragem de DataFrames

### Dificuldade

Ao tentar encontrar os pagamentos pendentes, criei uma condição que retornava True e False, mas não as linhas filtradas.

### O que aprendi

Uma condição como:

```python
df["status_pagamento"] == "Pendente"
```

gera uma série booleana.

Para obter somente as linhas correspondentes, é necessário utilizar essa condição dentro do DataFrame:

```python
df[df["status_pagamento"] == "Pendente"]
```

Isso ajudou a compreender melhor como os filtros funcionam no Pandas.

---

## 5. groupby() e sort_values()

### Dificuldade

Tive dificuldade para ordenar o resultado de um agrupamento.

### O que aprendi

Aprendi que, quando seleciono uma única coluna antes do sum(), o resultado pode ser uma Series. Nesse caso, a ordenação pode ser feita diretamente:

```python
df.groupby("cliente")["valor_bruto"].sum().sort_values(ascending=False)
```

Também compreendi melhor a diferença entre DataFrame e Series.

---

## 6. Conciliação de dados

### Dificuldade

No exercício de conciliação entre vendas e banco, precisei entender como identificar quais notas haviam sido pagas.

### O que aprendi

Aprendi a utilizar merge() para combinar DataFrames por uma coluna em comum e np.where() para criar uma classificação de status.

Exemplo:

```python
df_vendas.merge(df_banco, on="numero_nf", how="left")
```

e:

```python
np.where(
    df_conciliacao["valor_recebido"].notna(),
    "Pago",
    "Pendente"
)
```

Esse exercício mostrou uma aplicação prática de análise de dados em uma situação relacionada à área financeira.

---

## 7. SQL com Pandas

### Dificuldade

No início, tive dúvidas sobre como relacionar os comandos SQL com o que já havia aprendido em Pandas.

### O que aprendi

Percebi que vários conceitos possuem uma correspondência entre SQL e Pandas:

| SQL               | Pandas             |
| ----------------- | ------------------ |
| SELECT            | seleção de colunas |
| WHERE             | filtragem          |
| JOIN              | merge              |
| GROUP BY          | groupby            |
| SUM / COUNT / AVG | agregações         |
| ORDER BY          | sort_values        |

Essa comparação facilitou o entendimento do SQL.

---

## 8. Erros na construção das consultas SQL

### Dificuldade

Cometi erros como esquecer vírgulas entre colunas do SELECT e tive dúvidas sobre a ordem das cláusulas.

### O que aprendi

Passei a prestar atenção à estrutura da consulta:

```text
SELECT
FROM
JOIN
ON
WHERE
GROUP BY
HAVING
ORDER BY
```

Também aprendi a utilizar AS para criar nomes mais claros para os resultados:

```sql
SUM(valor) AS total_valor
```

---

## 9. SQL LIKE e NOT LIKE

### Dificuldade

Tive dúvida sobre a diferença entre LIKE e NOT LIKE.

### O que aprendi

LIKE localiza valores que correspondem ao padrão informado.

```sql
LIKE '%Venda%'
```

Já "NOT LIKE" exclui os valores que correspondem ao padrão:

```sql
NOT LIKE '%Venda%'
```

Também aprendi que `%` representa qualquer quantidade de caracteres.

---

## 10. Exportação e formatação no Excel

### Dificuldade

Depois de realizar as análises com Pandas e SQL, precisei entender como transformar os resultados em um arquivo Excel organizado.

### O que aprendi

Aprendi a utilizar:

* pd.ExcelWriter() para criar o arquivo e diferentes abas;
* openpyxl para editar a aparência do arquivo;
* Font para formatar fontes;
* PatternFill para preencher células;
* Alignment para alinhamento;
* number_format para formatar valores monetários;
* ajuste automático da largura das colunas.

Com isso, compreendi que o processo pode ser dividido em etapas:

**Pandas → tratamento dos dados**

**SQL → consultas e análises**

**ExcelWriter → exportação**

**Openpyxl → formatação**

---

## Conclusão

Os erros encontrados durante os exercícios não foram apenas problemas a serem corrigidos. Eles ajudaram a identificar quais conceitos ainda precisavam ser compreendidos.

O uso do NotebookLM como ferramenta de estudo permitiu consultar fontes, fazer perguntas, comparar explicações e transformar as dúvidas em novos exercícios práticos.

Esse processo contribuiu para desenvolver uma aprendizagem mais ativa, relacionando programação e análise de dados com situações da área contábil e financeira.
