# Prompts Utilizados no Processo de Aprendizagem

## Objetivo

Registrar os prompts utilizados durante o estudo com o NotebookLM e observar como diferentes formas de formular perguntas podem ajudar na compreensão dos conteúdos.

A utilização dos prompts teve como objetivo transformar o NotebookLM em uma ferramenta de apoio ao estudo, permitindo revisar conceitos, esclarecer dúvidas, criar exercícios e analisar dificuldades.

---

## 1. Revisão de conceitos

Um dos usos do NotebookLM foi solicitar explicações sobre conceitos estudados.

### Exemplo de prompt

> Explique este conteúdo de forma simples, como se eu estivesse aprendendo o assunto pela primeira vez. Dê exemplos práticos relacionados à contabilidade.

### Objetivo

Facilitar a compreensão de conceitos novos relacionando-os com conhecimentos prévios de contabilidade.

---

## 2. Comparação entre conceitos

Também foram utilizados prompts para relacionar conceitos de diferentes ferramentas.

### Exemplo de prompt

> Compare como uma determinada tarefa é realizada em Pandas e em SQL. Mostre a relação entre os comandos e explique quando cada abordagem pode ser utilizada.

### Objetivo

Perceber que diferentes ferramentas podem resolver problemas semelhantes utilizando estruturas diferentes.

---

## 3. Criação de exercícios

O NotebookLM também foi utilizado como apoio para transformar os conteúdos estudados em exercícios práticos.

### Exemplo de prompt

> Crie um exercício prático de análise de dados utilizando Pandas, relacionado a uma situação de contabilidade. Não mostre a resposta inicialmente. Depois que eu tentar, explique meus erros.

### Objetivo

Utilizar o conteúdo estudado de forma prática e testar a compreensão.

---

## 4. Aprendizagem a partir dos erros

Durante os exercícios, os erros foram utilizados como parte do processo de aprendizagem.

### Exemplo de prompt

> Analise meu erro e explique onde está o problema sem simplesmente fornecer a resposta. Mostre uma dica para que eu possa tentar novamente.

### Objetivo

Evitar apenas copiar a solução e desenvolver a capacidade de identificar e corrigir os próprios erros.

---

## 5. Organização do conhecimento

O NotebookLM também foi utilizado para organizar o conteúdo estudado.

### Exemplo de prompt

> Organize os principais conceitos que aprendi neste conteúdo em tópicos, destacando comandos, funções, exemplos e pontos que preciso revisar.

### Objetivo

Transformar o conteúdo estudado em material de consulta.

---

## 6. Registro das dificuldades

As dificuldades encontradas durante os exercícios também foram utilizadas como fonte de aprendizagem.

### Exemplo de prompt

> Com base nos exercícios realizados, identifique os principais pontos em que tive dificuldade e organize-os em uma lista de assuntos para revisão.

### Objetivo

Identificar lacunas de conhecimento e direcionar os próximos estudos.

---

## 7. Levantamento dos exercícios realizados

Para organizar o projeto no GitHub, foi utilizado um prompt para recuperar e organizar os exercícios realizados.

### Prompt utilizado

> Com base em todo o histórico das nossas conversas e no progresso registrado nas suas práticas, liste todos os exercícios práticos que realizei até agora. Para cada exercício, informe o objetivo, o que precisava ser feito, os principais erros ou dificuldades e o que aprendi com eles.

### Resultado

O levantamento permitiu organizar os exercícios em categorias como:

* Pandas;
* SQL;
* Excel/Openpyxl;
* aplicações relacionadas à contabilidade.

Esse levantamento foi utilizado como base para a organização da pasta exercicios deste repositório.

---

## O que aprendi sobre Prompt Engineering

Durante o processo, percebi que perguntas mais específicas produzem respostas mais úteis para o estudo.

Em vez de perguntar somente:

> "Explique Pandas."

é mais útil especificar o objetivo:

> "Explique este conceito de Pandas de forma simples, dê um exemplo relacionado à contabilidade e depois crie um exercício para eu praticar."

Também percebi que informar como quero aprender pode mudar a utilidade da resposta. Por exemplo, pedir uma **dica antes da solução** ajuda a transformar a ferramenta em apoio ao raciocínio, em vez de simplesmente entregar a resposta.

## Principais aprendizados

* Perguntas específicas ajudam a direcionar a resposta.
* Pedir exemplos práticos facilita a compreensão.
* Pedir exercícios permite transformar teoria em prática.
* Registrar erros ajuda a identificar pontos que precisam de revisão.
* Solicitar explicações passo a passo facilita o aprendizado de conceitos novos.
* O contexto da área de contabilidade pode ser utilizado para tornar os exercícios mais próximos de situações profissionais.

## Cicatrizes / dificuldades

Durante o processo de aprendizagem, algumas dificuldades foram importantes para entender melhor os conceitos.

Entre elas:

* diferença entre = e ==;
* utilização de & em filtros do Pandas;
* tratamento de valores NaN;
* diferença entre criar uma condição e efetivamente filtrar um DataFrame;
* diferença entre WHERE e HAVING;
* diferença entre LIKE e NOT LIKE;
* necessidade de utilizar print() para visualizar um DataFrame;
* compreensão da relação entre Pandas, SQL e Excel.

Essas dificuldades não foram tratadas apenas como erros, mas como parte do processo de aprendizagem e documentação do projeto.
