# Plugins com escopo restrito

Começamos com um repo de plugin por portal: `mcp-datos-uruguay` deveria
cobrir todo o portal de dados abertos do Uruguai. Ele ficou geral demais.
Um único repo tentando falar por cada dataset de um portal acaba
superficial em tudo e autoridade em nada.

Então dividimos. Criamos um repo focado,
[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben),
com escopo em um único domínio: o *Balance Energetico Nacional*, o balanço
energético nacional do Uruguai. O amplo `mcp-datos-uruguay` foi aposentado e
não está mais em uso.

## A lição

**Prefira um especialista de domínio a um generalista de portal de dados
abertos.** Um plugin é muito melhor quando a pessoa por trás dele entende
profundamente uma área temática, os dados de energia, seus termos, suas
peculiaridades, do que quando alguém sabe um pouco sobre cada dataset que
um portal por acaso publica.

O escopo restrito compensa de formas concretas:

- As descrições das ferramentas e as perguntas de exemplo são mais
  afiadas, porque são escritas por alguém que sabe o que as pessoas
  realmente perguntam.
- Um [glossário de domínio](glossary.md) é viável de construir e manter
  correto quando cobre um campo, não um portal inteiro.
- O repo permanece pequeno e fácil de manter, e domínios diferentes
  evoluem no seu próprio ritmo nos seus próprios repos.

Na dúvida, divida por domínio, não por portal nem por país.

Esta página é sobre *quem* deveria estar por trás de um plugin. Tão
importante quanto é *quando* essa pessoa entra: veja [especialistas de
domínio desde o primeiro dia](partners.md).
