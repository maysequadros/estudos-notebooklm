# Exercício — Auditoria de Notas Fiscais e Apuração Tributária

## Objetivo

Utilizar o Pandas para analisar notas fiscais, identificar situações de risco e realizar cálculos básicos de impostos de acordo com o regime tributário.

## O que precisava ser feito

1. Filtrar notas fiscais pendentes com valor bruto superior a R$ 5.000,00.
2. Criar uma coluna `imposto_devido`.
3. Aplicar uma alíquota de 6% para empresas do Simples Nacional.
4. Aplicar uma alíquota de 10% para empresas do Lucro Presumido.
5. Agrupar os dados por cliente e calcular os valores totais.

## Principais conceitos praticados

* Filtros com Pandas
* Operadores `==` e `&`
* `iterrows()`
* Condições `if` e `elif`
* Criação de novas colunas
* `groupby()`
* `sum()`
* `sort_values()`

## Código utilizado

```python
# Filtragem
pagamentos = df_notas[
    (df_notas["status_pagamento"] == "Pendente") &
    (df_notas["valor_bruto"] > 5000)
]

# Cálculo do imposto
impostos = []

for indice, linha in df_notas.iterrows():
    if linha["regime_tributario"] == "Simples Nacional":
        impostos.append(linha["valor_bruto"] * 0.06)

    elif linha["regime_tributario"] == "Lucro Presumido":
        impostos.append(linha["valor_bruto"] * 0.10)

df_notas["imposto_devido"] = impostos

# Agrupamentos
total_por_cliente = (
    df_notas
    .groupby("cliente")["valor_bruto"]
    .sum()
    .sort_values(ascending=False)
)

imposto_total = (
    df_notas
    .groupby("cliente")["imposto_devido"]
    .sum()
    .sort_values(ascending=False)
)
```

## Dificuldades encontradas

Durante o exercício, foi necessário compreender:

* a diferença entre `=` e `==`;
* como combinar duas condições utilizando `&`;
* a necessidade de colocar cada condição entre parênteses;
* como percorrer as linhas de um DataFrame com `iterrows()`;
* como armazenar os resultados de um cálculo em uma lista antes de criar uma nova coluna;
* como utilizar `groupby()` para consolidar informações.

## O que aprendi

Este exercício mostrou como o Pandas pode ser utilizado para automatizar análises que, em um processo contábil, poderiam ser realizadas manualmente em planilhas.

Também percebi que existem formas mais avançadas de realizar cálculos condicionais no Pandas, como `np.where()` e `apply()`. Neste exercício, o objetivo foi primeiro compreender a lógica utilizando estruturas que eu já conhecia.

## Aplicação na contabilidade

O exercício simula uma situação de análise fiscal e financeira de notas, permitindo identificar valores pendentes, calcular valores tributários de acordo com regras simplificadas e consolidar informações por cliente.
