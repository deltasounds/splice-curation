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
sharpening. If you change how something works, update `framework/curation-logic.md` so
the reasoning stays in sync with the mechanics.

## Keep the tone honest

This project is "here's how to make your credits usable," not a grievance about Splice.
Keep public writing accurate about who does what: Splice retrieves and downloads, Claude
organizes, the human judges. Don't imply Claude evaluates sound quality.

## Note the beta

The Splice connector is in beta. If you find a behavior change, add a dated note to
`framework/compatibility.md` rather than hard-coding around it.

Open a PR or an issue. Fork freely (MIT).
