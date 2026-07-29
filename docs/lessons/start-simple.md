# Start with a simple dataset

The clearest single piece of advice one pilot team offered in their
reflection session: if they did it again, they would begin with a
simpler dataset.

One of the pilots ran on a particularly challenging dataset. The
approach held up well under those conditions, and that was a valuable
stress test: it showed the architecture does not depend on the data
being easy. But the price was real. Producing reliable answers took
considerably more adaptation, fine-tuning and supporting tools than
expected, leaned heavily on [expert input](partners.md), and the
complexity of the data multiplied the cost of
[testing and validation](testing.md).

## The advice

Establish the approach on simple data first, then climb.

- **First dataset: simple.** Get the whole method working end to end
  on data that is easy to explain: the tools, the descriptions, the
  [glossary](glossary.md), the testing loop. Every problem you hit will
  be a problem of the method, not of the data.
- **Hard dataset second.** Once the method is established, a complex
  dataset becomes a stress test you choose, not a risk you discover
  mid-pilot.

This composes with [scope plugins narrowly](scope.md): a narrow domain
and a simple first dataset are the same instinct applied twice. Reduce
what you must explain to the machine until you can explain it well.
