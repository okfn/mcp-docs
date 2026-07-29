# Domain experts from day one

Running the same architecture twice gave us a clean comparison. In one
pilot, the data-owning team's experts were involved from the very
beginning. In the other, they joined later, and everything took longer.
Same architecture, same process, different starting lineup, and the
difference was visible.

The lesson, in the partner's own words: have the domain expert
available and involved **from the beginning**. The data owners cannot
arrive at the end.

[Scope plugins narrowly](scope.md) argues *who* should be behind a
plugin: someone who deeply understands one domain. This page is about
*when*. That person has to be in the room before the first tool is
written, because most of the work is [explaining the data to the
machine](meaning.md) and [checking the answers](testing.md), and both
need the expert, not the programmer.

## Picking the partner team

Choosing which institution and team hosts a pilot is a decision, not a
default. What the pilot experience suggests:

- **Pick the best team, not the nearest one.** The quality of the
  plugin is capped by how well the team behind the data knows it.
- **Pick a team that has time.** A partner squeezed for time can leave
  the pilot hanging mid-way, with no one available to validate answers
  or improve descriptions.
- **Senior management support matters.** Time only materialises when
  the team's leadership treats the pilot as real work, not a favour.

Only start when both the time and the institutional support are
actually there. If they are not, wait or pick another partner; a pilot
that stalls half-validated is worse than one that starts later.

Support is not only needed to start. Continuing after the pilot means
the work has to win a place on the organisation's own development
backlog, and that takes building support among the other internal data
teams, not just the one that hosted the pilot.

## The internal technical team too

Domain experts are not the only people to bring in early. One pilot's
technicians worked hands-on from the start, reading the repos and
running the server themselves, and after the pilot went on to
[build their own MCP server](ripple-effects.md). The other team, in
retrospect, would have involved their internal technical staff more
actively: working alongside the project team and replicating parts of
the process with the same tools and methodology.

Both experiences point at the same lesson. Documentation supports
future replication, but practical involvement is what transfers
knowledge and builds internal ownership. A team that only reads about
the pilot inherits a report; a team that works inside it inherits a
capability.

## The workload is real, and worth it

Be honest with the partner up front: hosting a pilot is extra work for
the data-owning team, on top of their normal duties. Validation and
polishing, not plumbing, is where most of that time goes.

It pays back. By the end of the pilot the data-owning team was motivated by
seeing their data used this way, and considered the result worth the
effort: a new tool of their own to keep polishing and eventually
publish, with clear warnings about its limitations.
