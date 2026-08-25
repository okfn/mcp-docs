# Design pattern: modular plugins

**Scope plugins by domain, not by portal.**

Plugins must be scoped to a single specific dataset or domain, for
example Uruguay's National Energy Balance repo,
[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben),
rather than attempting to cover an entire government open data portal
in one repository.

We learned this the hard way. The original `mcp-datos-uruguay` repo was
meant to cover Uruguay's whole open data portal, and it grew too
general: a single repo trying to speak for every dataset in a portal
ends up shallow everywhere and authoritative nowhere. It was retired in
favour of the focused energy-balance repo.

## Rationale

Portal-wide plugins become shallow generalists. Narrowing plugin
boundaries to a single domain provides key technical advantages:

- **Sharper tool descriptions.** Prompts and tool parameters are
  written specifically for the dataset's actual query patterns, by
  someone who knows what people actually ask.
- **Manageable glossaries.** Domain terminology and data dictionaries
  remain precise and feasible to maintain when they cover one field,
  not a whole portal.
- **Independent lifecycle.** Repositories stay small, clean and able to
  evolve at their own pace without breaking unrelated dataset tools.

## The rule of thumb

Prefer a domain expert over an open-data-portal generalist. A plugin is
far better when the person behind it deeply understands one subject
area - the energy data, its terms, its quirks - than when someone knows
a little about every dataset a portal happens to publish.

When in doubt, split by domain, not by portal or by country.
