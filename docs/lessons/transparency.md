# Transparency and trust

Several testers, independently, reported the same thing: the model mixes
its **general knowledge** with the **hard data** from the datasets,
without saying which is which. It was the most repeated negative
pattern.

## What we changed

We updated the system prompt to ask the model to always distinguish what
comes from the datasets from what comes from its general knowledge or its
own deductions. This mitigates the problem but does not remove the need
for the user to check.

## What to tell users

The most useful habit is to re-ask:

> "Is everything you just told me backed by the data you read, or by your
> training?"

In general the AI is honest here. It differentiates its sources better
when asked directly, and it often retracts when it realises it mixed a
general fact into a data answer and got something wrong.

## Confidence does not track evidence

A related and important point: the model's **tone of confidence does not
change with the quality of its evidence**. It answers with the same
assurance whether or not it actually has the data. Users cannot use
confidence as a signal of reliability, which is exactly why re-asking and
verifying matter.

This connects to the platform's core promise of
[traceability](../overview/idea.md): every answer should point to the
data it came from, so the user can check rather than trust the tone.
