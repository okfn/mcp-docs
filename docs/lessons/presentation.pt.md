# Tabelas e gráficos

As ferramentas MCP são construídas para sempre mostrar tabelas e
gráficos junto com a resposta. Os usuários valorizam muito isso, é o que
torna uma resposta verificável, mas vários testadores relataram o outro
lado: as tabelas e os gráficos às vezes estavam **repetidos ou verbosos
demais**.

## O que mudamos

Com base nesse feedback, tabelas e gráficos agora aparecem **minimizados
por padrão**. A informação continua lá, a um clique de distância, mas
não inunda mais a conversa.

## O que ainda está em aberto

Uma correção futura melhor é detectar quando a mesma tabela ou o mesmo
gráfico está sendo desenhado pela segunda vez e simplesmente não
repeti-lo. Essa deduplicação ainda não foi construída; por enquanto,
minimizar por padrão é a mitigação.
