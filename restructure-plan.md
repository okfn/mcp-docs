# Restructure plan (internal)

Working plan for applying `proposal.md` to the mkdocs site. Not part of
the published docs. Check items off as they land.

Companion documents:

- `proposal.md`: the proposed technical-docs structure (source of truth).
- `field-guide.md`: the non-technical companion; absorbs the lessons
  pages. Not yet published; its final home is still undecided.

## Decisions log

- Keep the CEPAL talk video and "What is in the box" on Home (the
  proposal's minimal Home dropped them; we preserve them).
- All `.es.md` / `.pt.md` files deleted and mkdocs i18n reduced to
  English only. Translations are re-done as the final pass, after the
  English content settles.
- Old `overview/*.md` files stay on disk, out of nav, so old URLs keep
  working until the final cleanup step.
- The "Lessons from the pilots" nav section stays (temporarily at top
  level) until step 7 retires it into the Field Guide.
- Correct the proposal's Brazil repo name: `mcp-datos-brasil-emendas`
  does not exist; the real plugin repo is `mcp-dados-brasil`.

## Steps

### Step 1: Introduction section + Home (DONE)

- [x] New `docs/introduction/context.md` ("Project context"): proposal
      text (pilots, risks, core technical principles).
- [x] New `docs/introduction/why-mcp.md` ("Why MCP?").
- [x] Rewrite `docs/index.md` per proposal Home, keeping the twin
      accuracy/traceability goals, the talk video, "What is in the
      box", "Where to go next" and the early-days note.
- [x] Nav: replace "The project" with "Introduction"; lift lessons to
      top level temporarily.
- [x] Drop non-English files and es/pt build config.

### Step 2: Architecture & design principles (DONE)

- [x] Rework `dev/architecture.md` as "System architecture": add the
      proposal's numbered execution flow and "Key technical rules";
      keep the mermaid sequence diagram (fills the proposal's diagram
      placeholder) and the two-replies explanation; fix links into
      `overview/` and `lessons/`.
- [x] New `dev/constraints.md` ("Architectural constraints"): stateless
      gateway + structured presentation, merged from
      `lessons/no-database.md` and `lessons/presentation.md`.
- [x] New `dev/design-pattern.md` ("Modular plugins"): scope by domain,
      from the proposal + `lessons/scope.md`.
- [x] Nav: "Architecture" becomes the "Architecture & design
      principles" subsection with the three pages.

### Step 3: Getting Started (DONE)

- [x] Nav move only: `dev/repositories.md` from Developer guide root to
      first entry of Getting started (after the section index).
- [x] Fix its link to `../lessons/scope.md` -> `design-pattern.md`.
- [x] `getting-started/*` pages unchanged.

### Step 4: Plugins -> "Building Plugins & Datasets" (DONE)

- [x] Rename nav section; reorder: plugin-info, yaml-datasets,
      python-tools, tool-results, connect, glossaries.
- [x] Append the "When to use YAML vs. Python" note to
      `plugins/yaml-datasets.md` (condensed from
      `lessons/yaml-tradeoff.md`); repoint its warning admonition.
- [x] New `plugins/glossaries.md` ("Implementing domain glossaries")
      from the proposal, absorbing `lessons/glossary.md`.
- [x] Fix links in `plugins/index.md` (scope, yaml-tradeoff, glossary,
      calculations, lessons index); retitle page "Building plugins and
      datasets".
- [x] `plugins/python-tools.md`: calculations rescue done early (was
      listed under step 7) - the precompute section now carries the
      full guidance from `lessons/calculations.md`, no lessons link.

### Step 5: Use Cases (was "Data catalogs") (DONE)

- [x] Nav: rename to "Use cases", promote to top level after Developer
      guide.
- [x] Rewrite `catalogs/index.md` from the proposal (technical
      highlights, "best used as", alpha status, fork-as-baseline).
      Used the real repo names (see decisions log).
- [x] Retitle `catalogs/uruguay.md` -> "Uruguay implementation",
      `catalogs/brasil.md` -> "Brazil implementation"; glossary and
      scope links repointed; lessons-index references now name the
      Field Guide with an interim lessons link (repoint in step 7).

### Step 6: Operations and Contributing (DONE)

- [x] Nav move only: both to top level, after Use cases. Content
      unchanged.

### Step 7: Retire the lessons section (DONE)

- [x] Rescue into the dev guide first:
      - [x] precomputed-calculations guidance from
        `lessons/calculations.md` -> section in
        `plugins/python-tools.md` (done in step 4);
      - [x] MCP resources from `lessons/resources.md` -> "Open data
        resources" section in `dev/architecture.md`.
- [x] Removed the lessons section from nav and deleted `docs/lessons/`
      (decision: the Field Guide is treated as published; another team
      owns it. The lesson sources remain in git history, and the
      content-gaps list below is the handoff to that team).
- [ ] Add the Field Guide link (Home, uruguay.md, brasil.md) when its
      URL exists. Style decision: the text assumes the Field Guide is
      published - no "until it is published" interim phrasing or
      fallback links to the lessons pages.

### Step 8: Cleanup and follow-ups

- [x] Deleted `docs/overview/` (nothing linked to it; replaced by the
      introduction section). `grep -rn "lessons/\|overview/" docs/`
      comes back clean and the build has zero warnings.
- [ ] Consider mkdocs-redirects for moved URLs (`overview/*`,
      `lessons/*`) since the site was live at the old paths.
- [x] Translation pass done: es/pt locales and nav_translations
      restored in mkdocs.yml; all 23 pages translated to both
      languages (46 files), reusing the pre-restructure translations
      (recovered from git, commit fec30c6) for terminology and
      register. Cross-page anchors preserved with explicit `{#...}`
      ids on translated headings. Trilingual build has zero warnings.

## Content gaps tracked separately

Gaps where neither `proposal.md` nor `field-guide.md` preserved current
content; owners of the Field Guide should pick these up:
`lessons/data-access.md` (data-governance checklist),
`lessons/ripple-effects.md` (adoption evidence), partner-selection
guidance from `lessons/partners.md`, the data-quality feedback loop
from `lessons/data-quality.md`, the Wikipedia impact story, the
"confidence does not track evidence" observation, and the field guide's
internal contradiction on traceability in its conclusion.
