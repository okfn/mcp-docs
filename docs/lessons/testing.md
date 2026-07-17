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

Two things that helped:

- Bringing **domain experts** into testing directly, rather than relying
  on generalists. See [scope plugins narrowly](scope.md).
- Making answers [traceable](../overview/open-model.md), so a tester can
  follow a number back to its source instead of guessing whether it is
  right.

Budget real time and real expertise for testing. It is not a formality
you can rush at the end.
