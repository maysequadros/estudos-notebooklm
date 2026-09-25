# Exercício — Agregações e Filtros Avançados em SQL

## Objetivo

Aprofundar os conhecimentos de SQL utilizando funções de agregação, filtros sobre resultados agrupados e buscas por padrões de texto.

## Exercício 1 — COUNT, AVG e ROUND

Calcular a quantidade de lançamentos e o valor médio por tipo de lançamento.

```sql
SELECT
    tipo,
    COUNT(*) AS qtd_transacoes,
    ROUND(AVG(valor), 2) AS valor_medio
FROM df_lancamentos
GROUP BY tipo;
```

### Conceitos praticados

* COUNT(*) → conta a quantidade de registros.
* AVG(valor) → calcula a média dos valores.
* ROUND(..., 2) → arredonda o resultado para duas casas decimais.
* AS → cria um nome para a coluna calculada.

---

## Exercício 2 — HAVING

Identificar os departamentos que possuem receita total superior a R$ 10.000,00.

```sql
SELECT
    nome_departamento,
    SUM(valor) AS total_receita
FROM df_lancamentos
JOIN df_centros
ON df_lancamentos.id_centro_custo = df_centros.id_centro_custo
WHERE tipo = 'Receita'
GROUP BY nome_departamento
HAVING SUM(valor) > 10000
ORDER BY SUM(valor) DESC;
```

### Conceito importante

O WHERE filtra registros **antes** do agrupamento.

O HAVING filtra os resultados **depois** do GROUP BY.

Essa diferença foi um dos principais aprendizados deste exercício.

---

## Exercício 3 — LIKE e NOT LIKE

Pesquisar registros de acordo com um determinado padrão de texto.

Exemplo utilizando LIKE:

```sql
SELECT *
FROM df_lancamentos
WHERE descricao LIKE '%Venda%';
```

O símbolo % representa qualquer quantidade de caracteres.

Por exemplo:

```text
Venda de Licenças
Venda de Treinamento
```

podem ser encontrados por:

```sql
LIKE '%Venda%'
```

Também foi testado o operador:

```sql
NOT LIKE '%Venda%'
```

Nesse caso, o resultado é o oposto: são retornados os registros que **não contêm** o termo "Venda".

## Dificuldade encontrada

Durante o exercício de busca por texto, inicialmente utilizei NOT LIKE quando o objetivo era localizar registros que continham a palavra "Venda".

Isso mostrou na prática a diferença entre:

```sql
LIKE
```

e

```sql
NOT LIKE
```

Em vez de considerar o erro apenas como algo a corrigir, ele foi registrado como parte do processo de aprendizagem.

## O que aprendi

Aprendi a utilizar funções de agregação para produzir informações resumidas e a diferença entre filtros de linhas e filtros de resultados agrupados.

Também aprendi que operadores aparentemente simples, como LIKE e NOT LIKE, podem alterar completamente o resultado de uma consulta.

## Resumo dos novos comandos

| Comando  | Função                        |
| -------- | ----------------------------- |
| COUNT()  | Conta registros               |
| AVG()    | Calcula média                 |
| ROUND()  | Arredonda valores             |
| HAVING   | Filtra resultados agrupados   |
| LIKE     | Pesquisa padrões de texto     |
| NOT LIKE | Exclui padrões de texto       |
| AS       | Cria um alias para uma coluna |

## Aplicação na contabilidade

Esses recursos podem ser utilizados para gerar indicadores financeiros, analisar médias de lançamentos, identificar departamentos com determinados volumes de receita ou despesa e localizar lançamentos por descrição ou categoria.
