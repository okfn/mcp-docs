# Strengths and weaknesses

## The headline conclusion

The system is fairly **deterministic when asked something very
specific**, like "what was value X in year Y?". As questions get more
open, the answers diverge more. Users should keep this in mind at all
times: **re-ask and verify.** These tools must be used with care.

## Strengths

- **Accurate on specific lookups.** When a question points at a value
  that exists in a dataset, behaviour is almost deterministic.
- **Honest about the edges of the data.** It generally states plainly
  when something is not in the BEN, instead of inventing it.
- **Recovers well from corrections.** When a user re-asks or flags an
  error, it recomputes, admits it, and fixes the answer.
- **The glossary helps.** Official BEN definitions, both consultable and
  [injected into the tools' context](glossary.md), improve answers and
  help non-experts.
- **Human-authored tables and charts** next to the AI's answer are
  highly valued and are the guarantee of accuracy.
- **Real, concrete usefulness.** Users put it to real work, for example
  improving a Wikipedia article.
- **It drives open data.** The pilot surfaces which datasets are missing
  and demands good documentation.
- **Simple to run.** No accounts, no database.

## Weaknesses

- **Derived calculations are not guaranteed.** Percentages and
  year-over-year changes were the only cases where wrong numbers were
  presented as data. See [reliability of calculations](calculations.md).
- **It blends model knowledge with dataset data** without flagging it.
  Mitigated by a [system prompt change](transparency.md), but still needs
  user verification.
- **Confident tone regardless of evidence.** It sounds equally sure with
  or without data.
- **Repeated or unnecessary tables and charts.** Mitigated by
  [minimising them by default](presentation.md).
- **No saved or shared conversations** without accounts, and no
  one-click download of a full answer.
- **Coverage depends on connected datasets.** Deeper questions go
  unanswered until more [data is opened and connected](data-quality.md).
- **Open questions diverge** and need user verification.
