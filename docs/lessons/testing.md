# Testing is not simple

Making sure the answers are actually correct turned out to be one of the
harder parts of the work, and it is easy to underestimate.

Verifying the quality of the information requires both **time** and
**domain knowledge**. You cannot check whether an answer about the
energy matrix is right unless you understand the energy matrix. That
puts the burden on scarce domain experts, not on whoever happens to be
building the software.

It is also not always easy to give feedback manually. A tester notices
that something feels off, but pinning down exactly which tool, which
dataset and which assumption produced the wrong number takes patient
work.

## Human review is not a phase, it is a requirement

The pilots did not surface a way around this. **People who understand
the data are needed to spot plausible but unsupported claims**, and that
need does not go away as the system improves. The failures that matter
are not the obvious ones; they are the answers that look right to
everyone except the person who knows the dataset.

Plan for continuous human review, not a review milestone you pass once.

## Real user questions beat invented ones

The most useful testing came from questions people actually ask. Pilot
partners handed us their frequently asked questions, and those became
test cases directly.

This worked better than test cases we wrote ourselves, in two ways: real
questions exposed where **tool descriptions** were unclear or
misleading, and they showed where the system needed **stronger limits**,
places it was answering when it should have declined.

If you run a pilot, ask your partner institution for their FAQ before
you write a single test.

## Who tests matters

Mixing testers from inside the partner government with testers from
civil society was useful precisely because they fail differently.
Insiders catch wrong figures. Outsiders catch answers that are
technically correct but incomprehensible, or that quietly assume
knowledge they do not have. See [two pilots](two-pilots.md).

Two things that helped:

- Bringing **domain experts** into testing directly, rather than relying
  on generalists. See [scope plugins narrowly](scope.md).
- Making answers [traceable](../overview/open-model.md), so a tester can
  follow a number back to its source instead of guessing whether it is
  right.

Budget real time and real expertise for testing. It is not a formality
you can rush at the end.
