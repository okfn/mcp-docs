# The YAML trade-off

Declaring datasets in YAML instead of writing Python looks like a great
idea: no code, just a tidy file per dataset. It works, and for a genuinely
simple dataset it is quick and pleasant. But it is a good idea to use
with care, and we ended up using far less YAML than we expected.

## Why

A declarative YAML format is, in the end, a **new query language**. To
express a real question you need engines, filters, formatters, response
templates, and rules for how they combine. Every capability a real
dataset asks for (a new kind of filter, a join, a computed column, a
special format) has to be added to that language and then learned by
whoever writes the YAML.

So the apparent simplicity moves rather than disappears. Instead of
writing a few lines of Python that any Python developer can read, you
write YAML in a bespoke dialect that only this project understands, and
when it does not stretch far enough you are stuck.

## Our rule of thumb

- **Really simple dataset**, a plain CSV with obvious aggregate or
  top-N questions? YAML is fine and fast.
- **Anything beyond that?** Reach for a [Python
  tool](../plugins/python-tools.md). It is clearer, more powerful, and
  it uses a language people already know instead of one we invented.

None of this makes YAML wrong. It makes it a sharp tool for a narrow job.
Use it for the simple cases, and do not try to grow it into a general
query language, because that is a language you would then have to
maintain.
