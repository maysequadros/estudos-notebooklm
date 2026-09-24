# Exercício — Conciliação de Vendas com Extrato Bancário

## Objetivo

Utilizar o Pandas para cruzar informações de vendas com recebimentos bancários e identificar quais vendas foram pagas ou permanecem pendentes.

## O que precisava ser feito

1. Cruzar a tabela de vendas com o extrato bancário.
2. Manter todas as vendas realizadas, mesmo quando não existisse um recebimento correspondente.
3. Criar uma coluna status_pagamento.
4. Classificar os registros como Pago ou `Pendente.
5. Filtrar somente os registros pendentes.

## Principais conceitos praticados

* merge()
* how="left"
* notna()
* np.where()
* filtros condicionais
* tratamento de valores nulos (`NaN`)

## Código utilizado

```python
df_conciliacao = df_vendas.merge(
    df_banco,
    on="numero_nf",
    how="left"
)

df_conciliacao["status_pagamento"] = np.where(
    df_conciliacao["valor_recebido"].notna(),
    "Pago",
    "Pendente"
)

df_pendentes = df_conciliacao[
    df_conciliacao["status_pagamento"] == "Pendente"
]
```

## Dificuldade encontrada

A principal dificuldade foi entender os valores NaN que apareceram depois do merge().

Quando uma venda não possuía um recebimento correspondente no banco, o campo valor_recebido ficava vazio (`NaN`).

A partir disso, foi utilizada a função notna() para verificar se existia um valor recebido.

## O que aprendi

Aprendi que o merge() permite cruzar informações de diferentes DataFrames utilizando uma coluna em comum.

Também aprendi que how="left" é útil quando quero manter todos os registros da tabela principal, mesmo quando não existe correspondência na outra tabela.

Além disso, aprendi a utilizar np.where() para transformar uma condição em uma classificação, neste caso:

* valor recebido existente → Pago
* valor recebido ausente → Pendente

## Aplicação na contabilidade

Esse tipo de procedimento pode ser utilizado para automatizar conciliações financeiras, identificando recebimentos que ainda não foram localizados no extrato bancário e facilitando o acompanhamento de valores pendentes.
