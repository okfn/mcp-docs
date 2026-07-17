# Reliability of calculations

This is the one area where testers reported answers that were
**numerically wrong but presented as data**. Direct lookups ("what was
value X in year Y?") were reliable. Derived calculations were not.

The risky question looks simple: "give me a table with the percentages
of X". The trouble is that X can range from a plain figure to something
that aggregates several other numbers, and the model has no guarantee of
getting the arithmetic right.

## How to mitigate it

The reliable fix is to not ask the model to do the maths. Precompute the
derived value with [Python and pandas](../plugins/python-tools.md) so it
becomes a real column in the dataset, and document that column. Then the
tool just reads it.

- **Simple cases** (a direct percentage of one dataset): add the
  percentage as a new column with pandas. Document what it means.
- **Complex cases** (a percentage that crosses several columns or
  datasets): precompute, again with pandas, the percentage people
  actually tend to ask for, for example "what share was renewable in
  year X?".
- **Hard, very specific cases** ("how much did X grow between year Y1
  and year Y2?"): too specific to precompute for every pair. A tool that
  acts as a small calculator might help here. We have not tested this
  yet.

## The takeaway

Treat any on-the-fly percentage or year-over-year change as suspect
until a tool computes it from a documented column. If a number matters,
it should come from the data, not from the model's head.
