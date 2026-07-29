# Sem contas, sem banco de dados

O piloto roda sem contas de usuário e sem banco de dados. Os usuários
não se registram, então não podemos salvar nem compartilhar conversas
inteiras. O que dá para fazer é baixar peças individuais: uma tabela, um
gráfico, ou uma das respostas da IA.

## O trade-off

Esta é uma escolha de design deliberada, e ela corta dos dois lados.

- **O benefício:** o sistema fica muito simples e muito fácil de
  instalar. Não há banco de dados para operar, fazer backup ou proteger,
  nem dados pessoais para cuidar.
- **O custo:** as conversas não podem ser salvas nem compartilhadas, e
  você não pode baixar uma resposta completa (texto mais tabelas mais
  gráficos) de uma só vez, apenas as peças.

Para um piloto, a simplicidade venceu, mas o lado do custo foi a
reclamação de produto mais repetida no feedback. Os testadores comparam
o chat com as ferramentas que usam todos os dias, ChatGPT ou Gemini, e
contra essa referência a falta de histórico e de compartilhamento é
sentida imediatamente.

Duas coisas para ter em mente ao pesar essa reclamação. Ser um produto
de chat completo nunca esteve no escopo do piloto. E o chat gateway é
apenas um cliente: o servidor MCP fala o protocolo padrão, então pode
ser plugado em outros clientes de chat que já oferecem contas, histórico
e compartilhamento. Se uma implantação futura precisar desses recursos
neste gateway, esse é o ponto em que adicionar armazenamento valeria o
peso extra.
