# Ferramentas novas, problemas antigos

Conectar uma IA a um portal de dados abertos é uma ferramenta nova e
reluzente, mas ela arrasta consigo um conjunto de questões muito antigas
de governança de dados. Nenhuma delas é sobre IA; todas decidem se as
respostas podem ser confiáveis.

- **Acesso direto ou uma cópia de leitura?** As ferramentas leem os
  dados abertos diretamente do portal, ou uma cópia separada somente de
  leitura? Cada escolha tem consequências para a atualidade dos dados e
  para a carga sobre o portal.
- **Os dados, ou uma visão deles?** Estamos servindo o dataset bruto ou
  alguma visão transformada dele, e essa transformação está documentada?
- **É a versão mais recente?** Um dataset em cache ou copiado pode ficar
  silenciosamente defasado em relação à fonte. Uma resposta baseada em
  dados desatualizados continua errada.
- **Estamos inflando as estatísticas do portal?** Se cada consulta bate
  no endpoint de dados abertos, podemos estar distorcendo as métricas de
  uso do próprio portal só por ler dados para responder perguntas.
- **Quais regras de negócio estão embutidas nos dados?** Os datasets são
  produzidos com suposições e regras incorporadas. Essas regras muitas
  vezes precisam ser explicadas ao usuário, ou o número fica fácil de
  interpretar mal.

A lição não é resolver tudo isso de uma vez, mas decidir cada ponto
deliberadamente para a sua implantação, e registrar a decisão por
escrito. Ferramentas novas não dispensam você das questões antigas.
