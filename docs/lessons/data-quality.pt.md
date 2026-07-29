# Qualidade e abertura dos dados

A coisa mais importante que o piloto nos mostrou não tem a ver com IA:
**ele é um forte incentivo para abrir dados bons e bem documentados.**

À medida que os usuários se aprofundavam, os especialistas de domínio
percebiam repetidamente que faltavam no portal datasets necessários para
responder às suas perguntas. Durante o piloto, cinco datasets de consumo
de energia por setor foram adicionados, e as respostas melhoraram muito.
Três dos cinco foram conectados a ferramentas MCP; os dois restantes
ficaram pendentes para a equipe do portal.

Essas ferramentas só funcionam quando os dados subjacentes têm boa
qualidade e estão bem documentados. Os dados deste piloto eram
excelentes, e essa é uma grande parte do motivo pelo qual funcionou.

Vale a pena transformar isso em uma precondição: **analisar a qualidade
e a documentação dos datasets candidatos antes de o piloto começar**, e
escolher dados que já sejam bons. O piloto vai revelar lacunas de
qualquer forma (o nosso revelou datasets cujas descrições precisavam ser
melhoradas, e a ausência de metadados é notada no momento em que uma
pergunta depende deles), mas um piloto deve aprofundar dados bons, não
resgatar dados ruins.

A qualidade tem duas metades, e ambas importam:

- **A qualidade dos dados** determina diretamente a qualidade das
  respostas.
- **A qualidade dos metadados** é o que torna a experiência didática:
  boas descrições, unidades e definições são o que permite ao assistente
  explicar um número em vez de apenas recitá-lo. É também por isso que
  um [glossário de domínio](glossary.md) compensa.

A metade dos metadados é também um desafio mais amplo para os provedores
de dados abertos. As descrições dos datasets muitas vezes não são tão
claras ou completas quanto precisam ser, especialmente em organizações
que gerenciam grandes quantidades de datasets, onde ninguém consegue
polir manualmente cada entrada. Melhorá-las é o que torna os datasets
mais fáceis de descobrir e interpretar, tanto para sistemas de IA quanto
para pessoas.

Há um **ciclo de retroalimentação positiva** escondido aqui. Quando os
especialistas de domínio conversam com a ferramenta, eles rapidamente
percebem que as respostas que faltam faltam porque os dados não estão
lá. Isso os incentiva a abrir mais dados, o que desbloqueia mais
respostas, o que convida a mais perguntas. A ferramenta se torna um
motor para a abertura de dados de qualidade.

## A cobertura é o roteiro

As respostas são calculadas apenas a partir dos datasets conectados,
então perguntas que vão além do que está conectado simplesmente ficam
sem resposta. Esse é o comportamento honesto que queremos (melhor um
claro "não está nos dados" do que um número inventado), mas significa
que o roteiro da ferramenta é na verdade o roteiro dos dados: a
cobertura cresce exatamente na mesma velocidade em que crescem os dados
abertos e documentados por trás dela. Continue integrando e conectando
novos datasets; é um trabalho de longo prazo que nenhum piloto resolve
sozinho.
