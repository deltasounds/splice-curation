# Contributing

This started as one person's way out of an unspent Splice credit balance, and it's more
useful the more taste and refinement the community folds in. Contributions welcome —
especially these:

## Add a profile

The highest-value contribution is a good, **transferable** profile in
`examples/profiles/`. Use the format in `framework/profile-format.md`. Keep public
examples grounded in descriptors, not artist names — the descriptors are what transfer.
Always include disqualifiers; a profile without them is too loose to triage against.

## Improve the framework

The calibration loop, the triage logic, and the search grammar are the parts most worth
sharpening. If you change how something works, update
[`framework/curation-logic.md`](framework/curation-logic.md) so the reasoning stays in
sync with the mechanics.

## Use the glossary's terms

[`framework/glossary.md`](framework/glossary.md) fixes one term per concept — *lane*,
*beat*, *commit boundary*, *signature*, *disqualifier*, *calibration*. Several docs
describe the same machinery from different angles, so a term that drifts in one place
quietly contradicts another. If you introduce or rename a concept, update the glossary in
the same PR.

One exception, and it's deliberate:
[`framework/project-instructions.md`](framework/project-instructions.md) is self-contained
because it gets pasted into a Claude project alone, with no access to this repo. What it
restates from other docs is load-bearing duplication — don't replace it with a
cross-reference.

## Keep the tone honest

This project is "here's how to make your credits usable," not a grievance about Splice.
Keep public writing accurate about who does what: Splice retrieves and downloads, Claude
organizes, the human judges. Don't imply Claude evaluates sound quality.

## Note the beta

The Splice connector is in beta. If you find a behavior change, add a dated note to
`framework/compatibility.md` rather than hard-coding around it.

## Which doc owns what

Each doc has a job. Edit the one that owns the thing you're changing:

| Doc | Owns |
|---|---|
| `framework/project-instructions.md` | The **operating rules** — what Claude actually does in a session |
| `framework/curation-logic.md` | The **rationale** — why the rules are shaped that way |
| `framework/profile-format.md` | The **profile schema** and how to write one |
| `framework/compatibility.md` | **Connector behavior** and dated change notes |
| `README.md` | **Orientation and setup** for someone arriving cold |
| `examples/session-walkthrough.md` | A **worked demonstration** of the six beats |

### Three things live in more than one place — sync them

`project-instructions.md` is pasted into a Claude project on its own and can't reference
the repo, so it must restate some things. That's intentional (see the note at the top of
that file). It does mean three concepts have copies that drift apart if you edit only one:

- **The division of labor** — Splice retrieves and downloads, Claude organizes, the human
  judges. In the README and the engine, and as a tone rule above.
- **Required core vs. optional post-processing.** In the README, the engine, and the
  logic doc.
- **The beta / intent-not-tool-mechanics stance.** In the README, the engine, and
  `compatibility.md`.

Change one, grep for the others. The six-beat arc also appears three times, but as
summary → spec → demo; those are different jobs and should read differently.

Open a PR or an issue. Fork freely (MIT).
