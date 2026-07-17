# Scope plugins narrowly

We started with one plugin repo per portal: `mcp-datos-uruguay` was
meant to cover Uruguay's whole open data portal. It grew too general.
A single repo trying to speak for every dataset in a portal ends up
shallow everywhere and authoritative nowhere.

So we split. We created a focused repo,
[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben),
scoped to a single domain: the *Balance Energetico Nacional*, Uruguay's
national energy balance. The broad `mcp-datos-uruguay` was retired and
is no longer in use.

## The lesson

**Prefer a domain expert over an open-data-portal generalist.** A plugin
is far better when the person behind it deeply understands one subject
area, the energy data, its terms, its quirks, than when someone knows a
little about every dataset a portal happens to publish.

Narrow scope pays off in concrete ways:

- Tool descriptions and sample questions are sharper, because they are
  written by someone who knows what people actually ask.
- A [domain glossary](glossary.md) is feasible to build and keep
  correct when it covers one field, not a whole portal.
- The repo stays small and easy to maintain, and different domains
  evolve at their own pace in their own repos.

When in doubt, split by domain, not by portal or by country.
