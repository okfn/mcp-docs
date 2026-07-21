# Data quality and openness

The single most important thing the pilot showed us is not about AI at
all: **it is a strong incentive to open good, well-documented data.**

As users pushed deeper, domain experts kept noticing that the portal was
missing datasets needed to answer their questions. During the pilot, five
datasets of energy consumption by sector were added, and answers improved
a lot. Three of the five were connected to MCP tools; the remaining two
were left pending for the Uruguay team.

These tools only work when the underlying data is good quality and well
documented. It is worth saying plainly that the data used in this pilot
was of excellent quality, and that is a large part of why it worked.

Quality has two halves, and both matter:

- **Data quality** shapes the quality of the answers directly.
- **Metadata quality** is what makes the experience didactic: good
  descriptions, units and definitions are what let the assistant explain
  a number instead of just reciting it. This is also why a
  [domain glossary](glossary.md) pays off.

There is a **positive feedback loop** hiding here. When domain experts
talk to the tool, they quickly see that the answers they are missing are
missing because the data is not there. That pushes them to open more
data, which unlocks more answers, which invites more questions. The tool
becomes an engine for opening quality data.

## Coverage is the roadmap

Answers are computed only from connected datasets, so questions that go
past what is connected simply get no answer. That is the honest
behaviour we want (better a clear "not in the data" than an invented
number), but it means the roadmap of the tool is really the roadmap of
the data: coverage grows exactly as fast as the open, documented data
behind it grows. Keep integrating and connecting new datasets; it is
long-term work that no single pilot resolves.
