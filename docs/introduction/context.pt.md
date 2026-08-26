# Contexto do projeto

**Conectando a IA a dados públicos abertos.**

Dados públicos abertos são essenciais para a transparência, a
prestação de contas e a tomada de decisões informada. No entanto,
extrair respostas dos portais oficiais muitas vezes exige navegar por
interfaces complexas, escrever consultas técnicas e gastar um tempo
considerável interpretando arquivos brutos.

Integrar a IA permite que os usuários consultem os dados usando
linguagem natural, mas os modelos de IA convencionais também
introduzem um risco grande: alucinações, números mal calculados e
erros de aparência plausível que minam a confiança na informação
oficial.

Para resolver isso, os
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/)
da Open Knowledge Foundation construíram uma ponte técnica aberta
usando o Model Context Protocol (MCP). Testamos essa abordagem em dois
datasets públicos reais:

- **Brasil**: emendas parlamentares (acompanhamento de fundos
  públicos).
- **Uruguai**: Balanço Energético Nacional (monitoramento da transição
  energética).

## Princípios técnicos centrais

- **Precisão e rastreabilidade.** As respostas devem se basear
  estritamente em datasets oficiais, e cada resposta deve apontar para
  sua fonte. O servidor garante essa regra no código.
- **Código simples em vez de linguagens sob medida.** As ferramentas
  são escritas como pequenas funções Python padrão. Datasets simples
  podem ser declarados em YAML sem escrever código.
- **Stack tecnológico simples e comprovado.** Construído sobre
  tecnologias de código aberto, padrão e confiáveis (Python, CSV,
  SQLite, HTML/JS puros). O sistema inteiro pode rodar localmente em
  um laptop, sem infraestrutura complexa.
- **Propriedade local.** Cada equipe mantém seu próprio repositório de
  plugin de forma independente, no seu idioma preferido e no seu
  próprio ritmo de releases.
