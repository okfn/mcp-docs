# Connecting the data is the easy part

If there is one headline lesson from both pilots, it is this: **getting
the model access to official data was not the hard part.**

The MCP layer does that job, and it does it reliably. Point the server
at a dataset, describe the tools, and the model can read real numbers
instead of recalling them.

But access is not understanding. A model that can read a column of
numbers still does not know:

- What the terms actually mean, in the official sense.
- What units the values are in.
- Which time period a figure covers, and whether periods are comparable.
- What the dataset deliberately leaves out.
- What assumptions were made when the data was compiled.

These are not supporting details you can add later for polish. **They
decide whether an answer is correct.** A right number under a wrong
label is a wrong answer.

## What this means in practice

Most of the real work in building a plugin is not plumbing, it is
explaining the data to the machine:

- Writing a [domain glossary](glossary.md) and injecting the official
  definitions into the tools' context, so the model has them when
  composing every answer.
- Writing tool and parameter descriptions that state units and periods
  explicitly, rather than assuming they are obvious.
- Being explicit about the limits of a dataset, so the model can say
  "not in the data" instead of reaching.
- Keeping plugins [scoped to a domain someone actually
  understands](scope.md), because nobody can write good descriptions for
  a portal they have not worked with.

This is also why [metadata quality matters as much as data
quality](data-quality.md). Budget for the meaning, not just the
connection.
