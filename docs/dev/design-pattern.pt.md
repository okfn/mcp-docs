# Padrão de design: plugins modulares

**Delimite os plugins por domínio, não por portal.**

Os plugins devem ter escopo em um único dataset ou domínio específico,
por exemplo o repo do Balanço Energético Nacional do Uruguai,
[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben),
em vez de tentar cobrir um portal governamental inteiro de dados
abertos em um só repositório.

Aprendemos isso do jeito difícil. O repo original `mcp-datos-uruguay`
deveria cobrir todo o portal de dados abertos do Uruguai, e ele ficou
geral demais: um único repo tentando falar por cada dataset de um
portal acaba superficial em tudo e autoridade em nada. Ele foi
aposentado em favor do repo focado no balanço energético.

## Justificativa

Plugins de portal inteiro se tornam generalistas superficiais.
Restringir as fronteiras do plugin a um único domínio traz vantagens
técnicas chave:

- **Descrições de ferramentas mais afiadas.** Os prompts e os
  parâmetros das ferramentas são escritos especificamente para os
  padrões reais de consulta do dataset, por alguém que sabe o que as
  pessoas realmente perguntam.
- **Glossários gerenciáveis.** A terminologia de domínio e os
  dicionários de dados permanecem precisos e viáveis de manter quando
  cobrem um campo, não um portal inteiro.
- **Ciclo de vida independente.** Os repositórios permanecem pequenos,
  limpos e capazes de evoluir no seu próprio ritmo sem quebrar
  ferramentas de datasets não relacionados.

## A regra prática

Prefira um especialista de domínio a um generalista de portal de dados
abertos. Um plugin é muito melhor quando a pessoa por trás dele
entende profundamente uma área temática - os dados de energia, seus
termos, suas peculiaridades - do que quando alguém sabe um pouco sobre
cada dataset que um portal por acaso publica.

Na dúvida, divida por domínio, não por portal nem por país.
