# Um modelo aberto para dados públicos

A plataforma é mais que código: é um modelo aberto para conectar a IA a
dados abertos governamentais, desenhado para que outros governos e
comunidades possam reutilizá-lo. Faz parte dos
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/)
da Open Knowledge Foundation, que transformam pilotos reais em métodos
abertos e replicáveis para uma IA responsável.

## Os dois objetivos

Tudo é medido contra dois objetivos, escolhidos porque são exatamente o
que um LLM sozinho não pode entregar:

- **Precisão**: a resposta é calculada a partir dos dados, não lembrada
  do treinamento. Um modelo que memorizou um número vai continuar
  recitando-o depois que o número mudar; uma ferramenta que lê o
  dataset, não.
- **Rastreabilidade**: a resposta carrega um link de volta para a
  fonte, para que o leitor possa conferi-la em vez de confiar nela. É
  isso que torna o sistema auditável por pessoas que não confiam nele,
  que é o único tipo de confiança que vale a pena ter para dados
  públicos.

Um alerta dos pilotos: um link para a fonte prova de onde vieram os
dados, não de onde veio o raciocínio. Veja [rastreabilidade é
necessária mas não suficiente](../lessons/transparency.md).

## Três eixos

**Colaboração.** O trabalho é uma colaboração entre membros da rede,
compartilhando problemas e soluções em vez de cada um construir
sozinho.

**Conhecimento aberto.** O desenvolvimento é de código aberto. O
conhecimento é compartilhado publicamente. O aprendizado é documentado,
traduzido e disponibilizado, de modo que o resultado é um modelo aberto
de boas práticas para conectar IA e dados abertos, não uma caixa-preta.

**Padronização.** As boas práticas estão embutidas no design do
servidor MCP. Governos enfrentam problemas parecidos com dados
parecidos, então há muito espaço para reutilização. O ideal que
buscamos é uma arquitetura plug-and-play: traga seus dados padronizados
e ganhe um assistente funcionando.

A alegação de reutilização já tem uma primeira prova de campo: depois
de um dos pilotos, os próprios técnicos do parceiro construíram um
servidor MCP sobre outra fonte de dados, sem que ninguém pedisse. Veja
[o que ficou depois do piloto](../lessons/ripple-effects.md).

## Para onde isso vai

Os pilotos alimentam um roadmap mais longo:

- Terminar a fase de testes dos pilotos e incorporar o feedback
  recebido.
- Documentar o aprendizado (este site é esse passo) e traduzi-lo.
- Fazer a documentação funcionar para equipes técnicas menos
  experientes e continuar publicando exemplos avançados funcionais. Os
  parceiros dos pilotos apontaram os dois: os exemplos como o que
  ajudou, a clareza extra como o que faltava.
- Publicar o material abertamente.
- Fazer crescer um kit de ferramentas reutilizável para dados
  padronizados, para que uma nova implantação comece de um template em
  vez de do zero.
