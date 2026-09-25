# Mini-Projeto — Fechamento Contábil e Exportação para Excel

## Objetivo

Desenvolver um pequeno fluxo de automação de relatório contábil utilizando Pandas, SQL e Excel.

O objetivo foi consultar os lançamentos contábeis, gerar diferentes visões dos dados e exportar os resultados para um arquivo Excel com abas separadas.

## Etapas do projeto

### 1. Detalhamento dos lançamentos

A primeira consulta relaciona os lançamentos aos respectivos departamentos e ordena os registros pelo valor.

```sql
SELECT
    id_lancamento,
    descricao,
    tipo,
    valor,
    nome_departamento
FROM df_lancamentos
JOIN df_centros
ON df_lancamentos.id_centro_custo = df_centros.id_centro_custo
ORDER BY valor DESC;
```

O resultado foi armazenado em um DataFrame:

```python
df_detalhado = sqldf(consulta_detalhada)
```

---

### 2. Resumo por departamento

A segunda consulta agrupou os lançamentos por departamento e tipo, calculando o valor total e a quantidade de transações.

```sql
SELECT
    nome_departamento,
    tipo,
    SUM(valor) AS total_valor,
    COUNT(*) AS qtd_transacoes
FROM df_lancamentos
JOIN df_centros
ON df_lancamentos.id_centro_custo = df_centros.id_centro_custo
GROUP BY nome_departamento, tipo;
```

O resultado foi armazenado em:

```python
df_resumo = sqldf(consulta_resumo)
```

---

### 3. Exportação para Excel

Os dois DataFrames foram exportados para um único arquivo Excel, utilizando duas abas diferentes.

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

As abas criadas foram:

* Lançamentos_Detalhados
* Resumo_Por_Depto

## Principais conceitos praticados

### Pandas

* DataFrames
* to_excel()
* ExcelWriter

### SQL

* SELECT
* JOIN
* ON
* GROUP BY
* SUM()
* COUNT()
* ORDER BY
* AS

### Excel / Openpyxl

Após a exportação, foi estudada a utilização do openpyxl para melhorar a apresentação do arquivo.

Foram praticados:

* abertura de um arquivo existente com load_workbook();
* acesso às planilhas utilizando wb e ws;
* formatação dos cabeçalhos;
* fonte em negrito;
* alinhamento;
* preenchimento de células;
* formato monetário;
* ajuste automático da largura das colunas;
* salvamento de uma nova versão do arquivo.

## Dificuldades encontradas

Uma das dúvidas surgiu quando uma consulta SQL foi executada, mas aparentemente não havia resultado na tela.

O problema não estava na consulta: o resultado havia sido armazenado no DataFrame, mas faltava utilizar:

```python
print(df_detalhado)
```

Isso reforçou a diferença entre **executar uma operação e visualizar o resultado dela**.

Outra etapa nova foi a utilização do openpyxl para aplicar formatação ao arquivo Excel gerado pelo Pandas.

## O que aprendi

Este exercício mostrou como diferentes ferramentas podem trabalhar juntas em um mesmo fluxo:

```text
Pandas
   ↓
organização dos dados
   ↓
SQL
   ↓
consulta e análise
   ↓
Pandas
   ↓
geração dos DataFrames
   ↓
ExcelWriter
   ↓
arquivo Excel
   ↓
Openpyxl
   ↓
formatação do relatório
```

Também aprendi que o Pandas pode ser utilizado não apenas para análise de dados, mas também como parte de um processo de automação de relatórios.

## Aplicação na contabilidade

Esse fluxo pode ser adaptado para situações como:

* fechamento contábil;
* relatórios financeiros;
* análise de receitas e despesas;
* acompanhamento por centro de custo;
* conciliações;
* preparação de informações para análise gerencial.

## Evolução do aprendizado

Este mini-projeto representa uma evolução em relação aos exercícios anteriores.

Nos primeiros exercícios, o foco estava em aprender comandos individuais.

Neste projeto, os conhecimentos começaram a ser combinados em um fluxo mais próximo de uma aplicação prática:

**dados → análise → consulta → consolidação → relatório.**
