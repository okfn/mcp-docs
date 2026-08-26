# Restrições arquiteturais

Duas escolhas deliberadas de design moldam a plataforma. As duas são
trade-offs, feitos conscientemente, e as duas receberam feedback real
dos usuários durante os pilotos.

## Gateway sem estado: sem contas, sem banco de dados

**Escolha de design.** O sistema opera sem contas de usuário, registro
de sessões ou um banco de dados central. Os usuários podem baixar
saídas individuais (tabelas, gráficos ou blocos de texto), mas as
conversas inteiras não são salvas nem compartilhadas do lado do
servidor.

**Trade-off.** Isso elimina a administração de banco de dados, a
conformidade com retenção de dados e a sobrecarga de gestão de
usuários, mantendo o servidor leve e fácil de implantar: não há banco
de dados para operar, fazer backup ou proteger, nem dados pessoais
para cuidar.

O custo também é real. A falta de histórico de chat foi a reclamação
de produto mais repetida no feedback do piloto: os testadores comparam
o chat com as ferramentas que usam todos os dias, e contra essa
referência a falta de histórico e de compartilhamento é sentida
imediatamente.

Duas coisas para ter em mente ao pesar essa reclamação. Ser um produto
de chat completo nunca esteve no escopo. E o chat gateway é apenas um
cliente: o servidor MCP segue o protocolo padrão, então pode ser
plugado em clientes de chat de terceiros já existentes, que já cuidam
de gestão de contas, histórico e compartilhamento. Se uma implantação
futura precisar desses recursos neste gateway, esse é o ponto em que
adicionar armazenamento valeria o peso extra.

## Apresentação estruturada: tabelas e gráficos

**Escolha de design.** As ferramentas retornam dados estruturados
(tabelas e gráficos) junto com as respostas em texto, para garantir
que as respostas sejam auditáveis e verificáveis. Os usuários
valorizam muito isso; é o que torna uma resposta conferível contra a
fonte.

**Mitigação na interface.** O outro lado, relatado por vários
testadores do piloto, é que as tabelas e os gráficos às vezes estavam
repetidos ou verbosos demais. As saídas estruturadas são, portanto,
renderizadas minimizadas por padrão na interface: os registros
completos da fonte ficam a um clique de distância sem inundar o fluxo
da conversa.

Uma correção futura melhor é detectar quando a mesma tabela ou o mesmo
gráfico está sendo desenhado pela segunda vez e simplesmente não
repeti-lo. Essa deduplicação ainda não foi construída; por enquanto,
minimizar por padrão é a mitigação.
