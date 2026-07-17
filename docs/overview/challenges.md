# The challenge

The question that started the project:

> How can we bring the latest AI (large language models) to open data
> portals **without compromising trust in public information**?

It is harder than it sounds, because using an LLM on its own runs into
several problems at once.

## LLMs are not built to tell the truth

Their output is an estimate. Bias, gaps in training data and
architectural limits mean a fluent answer is not necessarily a correct
one. Accuracy is not something you get for free.

## You cannot see why they answer what they answer

Even when a model shows its "reasoning", that does not solve the
problem: it just hands the job of checking the truth to the citizen.
And because models are non-deterministic, the same question can produce
a different chain of reasoning each time.

## They are unreliable at the mechanical parts

LLMs are not good at writing correct SQL against real databases, and
more generally they are not the "intelligence" the marketing suggests.
Our design leans on this fact rather than fighting it: the model never
writes the query. It picks from predefined [tools](../plugins/index.md)
that run vetted queries, so the data work is done by code, not guessed
by the model.

## They will not say "I do not know"

Some models are aggressively helpful: given a question, they will
torture whatever data is at hand until it yields an answer that seems to
satisfy the question. Not knowing how to say "I do not have that" is
itself a source of wrong answers.

## Our response

We do not try to make the LLM trustworthy on its own. We put it behind
a layer of tools over real data, aiming for two things the model cannot
guarantee alone: [accuracy and traceability](open-model.md). The model
handles language; the data handles facts.
