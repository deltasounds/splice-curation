# Splice Curation

A lightweight framework for spending down a Splice credit balance **selectively and
fast** — turning stranded credits into a compact, useful sample library before your
subscription renews. It runs entirely on Splice's official (beta) MCP connector for
Claude. No browser automation, no workarounds, nothing that touches Splice's terms.

The idea in one line: **human taste, accelerated mechanics.** You stay the curator.
The framework accelerates everything around your judgment — searching, triaging,
tracking, filing — without ever bulk-dumping samples you don't want.

## Who this is for

Anyone sitting on a pile of Splice credits who finds the one-at-a-time download flow too
slow to work through, but doesn't want to just grab whole 300-sample packs where most of
it goes unused. If that's you, this gets your credits usable again.

> **Note on the Splice connector:** it's officially provided by Splice and currently in
> beta, so its exact tools may change. This framework is written around *intent* (search
> by feel → triage → audition → confirm → download) rather than specific tool behavior,
> so it should survive updates. See `framework/compatibility.md`.

## Zero to first download

1. **Enable the Splice connector** in Claude. Splice's own setup guide is the source of
   truth for the connector URL and login:
   https://splice.com/tools/mcp-server
2. **Create a dedicated Claude project** for this (not just a chat thread — the project
   is what makes your setup persist).
3. **Paste `framework/project-instructions.md`** into the project's instructions. That's
   the engine.
4. **Add a profile or two.** Copy `personal/my-taste.example.md` to a private file and
   fill in one signature and one profile using `framework/profile-format.md`. You can
   start with the generic examples in `examples/profiles/`.
5. **Run one session.** Tell the project what you want — e.g. *"twenty punchy kicks"* —
   and it walks you through the six-beat arc, confirming the exact files and credit cost
   before anything is spent.

That's it. You're curating.

## How it works (the short version)

- **Search grammar, three optional layers:** Function (kick, loop, texture…) ×
  Signature (your named vibes) × Constraints (BPM, key, one-shot/loop… — optional).
- **Two lanes:** *trusted* (batch-approve after a quick scan) and *review* (audition
  each). You pick per search.
- **One hard commit boundary:** nothing spends a credit until you see exact filenames,
  count, and cost, and say go.
- **Six-beat session arc:** Intent → Search translation → Triage → Audition/approval →
  Download & filing → **Calibration**.
- **Calibration** folds your session verdicts back into your profiles, so the system
  gets more accurate the more you use it.

Full reasoning is in `framework/curation-logic.md`.

## Who does what

- **Splice** retrieves and ranks the catalog, and performs the licensed download.
- **Claude** translates intent, triages on metadata, holds session state, organizes
  the workflow.
- **You** audition and make every aesthetic call.

Claude does not judge sound quality — it filters on metadata and descriptions. You're
the ears.

## What's guaranteed vs. environment-dependent

- **Required core**, works on the connector alone: search → review → approve → download.
- **Optional post-processing**, depends on your Claude environment's filesystem access:
  rename → organize → deduplicate → manifest. Splice describes using Claude Cowork to
  scan and organize a local library, so this is real but not guaranteed everywhere.

## Repo layout

```
README.md                     ← you are here
LICENSE                       ← MIT
CONTRIBUTING.md               ← how to contribute (profiles especially welcome)
framework/
  project-instructions.md     ← paste this into your Claude project (the engine)
  curation-logic.md           ← the reasoning, for anyone forking it
  profile-format.md           ← the profile format + a worked example
  compatibility.md            ← notes on the beta connector
examples/
  profiles/                   ← generic, transferable profile examples
personal/
  my-taste.example.md         ← template for your private taste file (keep yours out of git)
```

## Licence

MIT — see `LICENSE`. Fork it, improve it, share your profiles back.
