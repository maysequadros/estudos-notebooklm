# Prompts Utilizados e Estratégias de Aprendizagem

## Objetivo

Este arquivo registra as estratégias de formulação de perguntas utilizadas durante o processo de aprendizagem com o NotebookLM.

Os prompts foram utilizados como apoio para revisar conceitos, esclarecer dúvidas, criar exercícios, organizar conhecimentos e identificar pontos que precisavam de revisão.

> **Observação:** os exemplos abaixo representam as estratégias de prompting utilizadas no processo de estudo. Eles não têm necessariamente a finalidade de reproduzir palavra por palavra todas as perguntas feitas durante as conversas.
---

## 1. Revisão de conceitos

Uma das estratégias utilizadas foi solicitar explicações de conceitos de forma simples, especialmente quando um assunto era novo ou ainda não estava totalmente compreendido.

### Exemplo de estratégia

> Explique este conteúdo de forma simples, como se eu estivesse aprendendo o assunto pela primeira vez. Dê exemplos práticos relacionados à contabilidade.

### Objetivo

Facilitar a compreensão de conceitos novos e relacioná-los com conhecimentos prévios da área contábil.

---

## 2. Comparação entre conceitos

Outra estratégia foi relacionar conceitos de diferentes ferramentas para compreender melhor suas semelhanças e diferenças.

### Exemplo de estratégia

> Compare como uma determinada tarefa é realizada em Pandas e em SQL. Mostre a relação entre os comandos e explique quando cada abordagem pode ser utilizada.

### Objetivo

Compreender que diferentes ferramentas podem resolver problemas semelhantes utilizando estruturas diferentes.

Essa estratégia foi especialmente útil para relacionar conceitos como:

* filtragem e WHERE;
* merge() e JOIN;
* groupby() e GROUP BY;
* sort_values() e ORDER BY.

---

## 3. Criação de exercícios

O NotebookLM também foi utilizado como apoio para transformar conteúdos estudados em exercícios práticos.

### Exemplo de estratégia

> Crie um exercício prático de análise de dados utilizando Pandas, relacionado a uma situação de contabilidade. Não mostre a resposta inicialmente. Depois que eu tentar, explique meus erros.

### Objetivo

Transformar teoria em prática e testar a compreensão dos conceitos.

---

## 4. Aprendizagem a partir dos erros

Os erros encontrados durante os exercícios foram utilizados como parte do processo de aprendizagem.

### Exemplo de estratégia

> Analise meu erro e explique onde está o problema sem simplesmente fornecer a resposta. Mostre uma dica para que eu possa tentar novamente.

### Objetivo
Evitar apenas copiar a solução e desenvolver a capacidade de identificar e corrigir os próprios erros.

Essa estratégia está relacionada à forma como os exercícios foram desenvolvidos: primeiro tentar resolver, identificar o ponto de dificuldade e depois compreender a correção.

5. Organização do conhecimento

O NotebookLM também foi utilizado para organizar conteúdos estudados em materiais de consulta.

Exemplo de estratégia

Organize os principais conceitos que aprendi neste conteúdo em tópicos, destacando comandos, funções, exemplos e pontos que preciso revisar.

Objetivo

Transformar conteúdos estudados em materiais organizados para futuras revisões.

6. Identificação de dificuldades

As dificuldades encontradas durante os exercícios foram utilizadas para identificar assuntos que precisavam de maior atenção.

Exemplo de estratégia

Com base nos exercícios realizados, identifique os principais pontos em que tive dificuldade e organize-os em uma lista de assuntos para revisão.

Objetivo

Identificar lacunas de conhecimento e direcionar os próximos estudos.

Variação de prompts

Durante o processo, foi possível perceber que uma pergunta mais específica tende a ser mais útil para o objetivo de aprendizagem.

Por exemplo, uma solicitação genérica:

Explique Pandas.

pode ser transformada em uma solicitação mais direcionada:

Explique este conceito de Pandas de forma simples, dê um exemplo relacionado à contabilidade e depois crie um exercício para eu praticar.

A segunda formulação define melhor:

o assunto;
o nível de explicação desejado;
o contexto;
a aplicação prática;
a atividade que deverá ser realizada.

Também foi útil especificar como eu queria aprender, por exemplo, solicitando uma dica antes da solução.

O que aprendi sobre Prompt Engineering

Durante o processo, percebi que perguntas específicas ajudam a direcionar melhor a resposta.

Também percebi que incluir contexto da área de contabilidade pode tornar os exemplos mais próximos das aplicações que pretendo estudar.

Outra estratégia importante foi pedir que a ferramenta não entregasse imediatamente a solução, permitindo primeiro tentar resolver o exercício e utilizar a resposta posteriormente para compreender o erro.

Assim, o prompt deixa de ser apenas uma solicitação de informação e passa a fazer parte do processo de aprendizagem.

Principais aprendizados
Perguntas específicas ajudam a direcionar a resposta.
Pedir exemplos práticos facilita a compreensão.
Pedir exercícios permite transformar teoria em prática.
Registrar erros ajuda a identificar pontos que precisam de revisão.
Solicitar explicações passo a passo facilita o aprendizado de conceitos novos.
O contexto da área de contabilidade pode tornar os exercícios mais próximos de situações profissionais.
Pedir dicas antes da solução ajuda a preservar a participação ativa no processo de resolução.
Cicatrizes e dificuldades

Durante o processo de aprendizagem, algumas dificuldades foram importantes para compreender melhor os conceitos.

Entre elas:

diferença entre = e ==;
utilização de & em filtros do Pandas;
tratamento de valores ausentes (NaN);
diferença entre criar uma condição e efetivamente filtrar um DataFrame;
diferença entre WHERE e HAVING;
diferença entre LIKE e NOT LIKE;
necessidade de utilizar print() para visualizar determinados resultados;
compreensão da relação entre Pandas, SQL e Excel.

Essas dificuldades foram utilizadas como oportunidades de revisão e ajudaram a transformar erros em novos aprendizados.

Relação com o projeto

As estratégias de prompting contribuíram para transformar o NotebookLM em uma ferramenta de apoio ao estudo, enquanto os exercícios e registros de dificuldades ajudaram a consolidar os conhecimentos.

O resultado desse processo está organizado nas demais partes do repositório:

notas/ — resumos, fontes, glossário e dificuldades;
exercicios/ — atividades práticas;
prompts/ — estratégias de prompting utilizadas durante o processo.
