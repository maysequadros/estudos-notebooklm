notas/pandas-vs-sql.md
PANDAS + SQL + OPENPYXL

GERAÇÃO E FORMATAÇÃO DE RELATÓRIOS EXCEL

==================================================

1. FLUXO GERAL

--------------------------------------------------

Pandas

→ cria e manipula os dados

SQL

→ consulta, cruza, agrupa e resume os dados

ExcelWriter

→ cria um arquivo Excel com várias abas

openpyxl

→ abre o Excel e aplica formatação

Resultado:

→ relatório Excel organizado e profissional

FLUXO:

Dados

↓

DataFrame

↓

SQL / consultas

↓

Relatórios

↓

Excel

↓

openpyxl

↓

Formatação

↓

Excel final

==================================================

2. CRIAR O EXCEL COM VÁRIAS ABAS

==================================================

Usamos:

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

CONCEITOS:

pd.ExcelWriter()

→ cria/gerencia um arquivo Excel

sheet_name=

→ nome da aba

index=False

→ não exporta o índice do Pandas

RESULTADO:

arquivo.xlsx

├── Lançamentos_Detalhados

└── Resumo_Por_Depto

==================================================

3. ABRIR O EXCEL COM OPENPYXL

==================================================

Depois que o Excel foi criado:

import openpyxl

wb = openpyxl.load_workbook("arquivo.xlsx")

CONCEITO:

load_workbook()

→ abre um arquivo Excel existente

wb

→ representa o arquivo Excel inteiro

(Workbook)

PARA ACESSAR UMA ABA:

ws = wb["Lançamentos_Detalhados"]

CONCEITO:

wb → arquivo Excel inteiro

ws → uma aba específica

(Worksheet)

==================================================

4. PRINCIPAIS ESTILOS DO OPENPYXL

==================================================

PatternFill

→ cor/fundo da célula

Font

→ fonte, tamanho, negrito e cor

Alignment

→ alinhamento do conteúdo

Border

→ bordas

number_format

→ formato de números/moeda

IMPORTS:

from openpyxl.styles import (

Font,

PatternFill,

Alignment,

Border,

Side

)

from openpyxl.utils import get_column_letter

==================================================

5. ESTILO DO CABEÇALHO

==================================================

CRIAR COR DE FUNDO:

estilo_cabecalho = PatternFill(

start_color="1F4E79",

end_color="1F4E79",

fill_type="solid"

)

CRIAR FONTE:

fonte_cabecalho = Font(

name="Calibri",

size=11,

bold=True,

color="FFFFFF"

)

CRIAR ALINHAMENTO:

alinhamento_centro = Alignment(

horizontal="center",

vertical="center"

)

SIGNIFICADO:

PatternFill

→ fundo azul

Font

→ texto branco e negrito

Alignment

→ texto centralizado

==================================================

6. APLICAR FORMATAÇÃO AO CABEÇALHO

==================================================

Para trabalhar com várias abas:

for nome_aba in [

"Lançamentos_Detalhados",

"Resumo_Por_Depto"

]:

ws = wb\[nome_aba\]

for cell in ws\[1\]:

    cell.fill = estilo_cabecalho

    cell.font = fonte_cabecalho

    cell.alignment = alinhamento_centro

IMPORTANTE:

ws[1]

→ representa a primeira linha

for cell

→ percorre cada célula da primeira linha

ATENÇÃO:

for cell in ws

→ percorre as linhas da planilha

for cell in ws[1]

→ percorre as células da primeira linha

==================================================

7. FORMATO MONETÁRIO

==================================================

Formato:

'R$ #,##0.00'

ABA Lançamentos_Detalhados:

A = id_lancamento

B = descricao

C = tipo

D = valor

E = nome_departamento

Como "valor" está na coluna D:

for cell in wb["Lançamentos_Detalhados"]["D"][1:]:

cell.number_format = 'R$ #,##0.00'

ABA Resumo_Por_Depto:

A = nome_departamento

B = tipo

C = total_valor

D = qtd_transacoes

Como "total_valor" está na coluna C:

for cell in wb["Resumo_Por_Depto"]["C"][1:]:

cell.number_format = 'R$ #,##0.00'

[1:]

→ começa depois do cabeçalho

==================================================

8. AJUSTAR LARGURA DAS COLUNAS

==================================================

Objetivo:

→ evitar texto cortado

→ evitar números aparecendo como ###

→ deixar o relatório organizado

CÓDIGO:

for nome_aba in [

"Lançamentos_Detalhados",

"Resumo_Por_Depto"

]:

ws = wb\[nome_aba\]

for col in ws.columns:

    max_len = max(

        len(str(cell.value or ""))

        for cell in col

    )

    col_letter = get_column_letter(

        col\[0\].column

    )

    ws.column_dimensions\[

        col_letter

    \].width = max(max_len + 4, 14)

LÓGICA:

1. Percorre cada coluna

2. Descobre o maior conteúdo

3. Converte o número da coluna para letra

4. Define a largura

5. Garante largura mínima de 14

get_column_letter()

→ transforma número da coluna em letra

1 → A

2 → B

3 → C

4 → D

==================================================

9. SALVAR O EXCEL FORMATADO

==================================================

Depois de todas as alterações:

wb.save(

"Fechamento_Contabil_Formatado.xlsx"

)

IMPORTANTE:

arquivo.xlsx

→ arquivo original

Fechamento_Contabil_Formatado.xlsx

→ arquivo final formatado

==================================================

10. ESTRUTURA COMPLETA

==================================================

# 1. Criar Excel com Pandas

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

# 2. Abrir Excel

wb = openpyxl.load_workbook("arquivo.xlsx")

# 3. Criar estilos

estilo_cabecalho = PatternFill(

start_color="1F4E79",

end_color="1F4E79",

fill_type="solid"

)

fonte_cabecalho = Font(

name="Calibri",

size=11,

bold=True,

color="FFFFFF"

)

alinhamento_centro = Alignment(

horizontal="center",

vertical="center"

)

# 4. Formatar cabeçalhos

for nome_aba in [

"Lançamentos_Detalhados",

"Resumo_Por_Depto"

]:

ws = wb\[nome_aba\]

for cell in ws\[1\]:

    cell.fill = estilo_cabecalho

    cell.font = fonte_cabecalho

    cell.alignment = alinhamento_centro

# 5. Formatar valores monetários

for cell in wb["Lançamentos_Detalhados"]["D"][1:]:

cell.number_format = 'R$ #,##0.00'

for cell in wb["Resumo_Por_Depto"]["C"][1:]:

cell.number_format = 'R$ #,##0.00'

# 6. Ajustar largura

for nome_aba in [

"Lançamentos_Detalhados",

"Resumo_Por_Depto"

]:

ws = wb\[nome_aba\]

for col in ws.columns:

    max_len = max(

        len(str(cell.value or ""))

        for cell in col

    )

    col_letter = get_column_letter(

        col\[0\].column

    )

    ws.column_dimensions\[

        col_letter

    \].width = max(max_len + 4, 14)

# 7. Salvar

wb.save(

"Fechamento_Contabil_Formatado.xlsx"

)

==================================================

11. RESUMO PARA CONSULTA RÁPIDA

==================================================

Pandas

→ trabalha com os dados

SQL

→ consulta e transforma os dados

ExcelWriter

→ cria Excel com várias abas

openpyxl

→ abre e formata Excel

wb

→ arquivo Excel inteiro

ws

→ uma aba do Excel

PatternFill

→ fundo

Font

→ texto

Alignment

→ alinhamento

Border

→ bordas

number_format

→ formato de números/moeda

get_column_letter()

→ número da coluna → letra

wb.save()

→ salva as alterações

==================================================

12. ORDEM PARA NÃO SE PERDER

==================================================

1. Criar DataFrames

    ↓

2. Fazer consultas SQL

    ↓

3. Criar os relatórios

    ↓

4. Exportar com ExcelWriter

    ↓

5. Abrir com openpyxl

    ↓

6. Selecionar as abas com wb["nome"]

    ↓

7. Criar estilos

    ↓

8. Formatar cabeçalhos

    ↓

9. Formatar valores monetários

    ↓

10. Ajustar largura das colunas

    ↓

11. Salvar com wb.save()

==================================================

13. IDEIA PRINCIPAL

==================================================

PANDAS = DADOS

SQL = CONSULTAS

EXCELWRITER = EXPORTAÇÃO

OPENPYXL = FORMATAÇÃO

JUNTANDO OS QUATRO:

DADOS

→ ANÁLISE

→ RELATÓRIO

→ EXCEL

→ FORMATAÇÃO PROFISSIONAL
