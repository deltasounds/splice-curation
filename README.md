# Splice Curation

A lightweight framework for spending down a Splice credit balance **selectively and
fast** — turning stranded credits into a compact, useful sample library before your
subscription renews. It runs entirely on Splice's official (beta) MCP connector for
Claude. No browser automation, no workarounds, nothing that touches Splice's terms.

The idea in one line: **human taste, accelerated mechanics.** You stay the curator.
The framework accelerates everything around your judgment — searching, triaging,
tracking, filing — without ever bulk-dumping samples you don't want.

📖 **Want the reasoning rather than the setup?** Read
**[How the curation logic works](framework/curation-logic.md)** — why taste needs
disqualifiers, why "trusted" never means "no review", and why a curation system that
doesn't learn from its own verdicts stays as good as its first draft forever. That's the
part worth stealing even if you never touch Splice.

## Who this is for

Anyone sitting on a pile of Splice credits who finds the one-at-a-time download flow too
slow to work through, but doesn't want to just grab whole 300-sample packs where most of
it goes unused. If that's you, this gets your credits usable again.

> **Note on the Splice connector:** it's officially provided by Splice and currently in
> beta, so its exact tools may change. This framework is written around *intent* (search
> by feel → triage → audition → confirm → download) rather than specific tool behavior,
> so it should survive updates. See [`framework/compatibility.md`](framework/compatibility.md).

## How this repo relates to Claude

**Claude never reads this repo.** There's no clone step, no sync, no integration. These
files are text you copy into a Claude project **once, by hand**. The repo exists to
version the framework and share it; the running system lives in your Claude project.

Two files make the round trip:

| This repo | Goes where | What it does |
|---|---|---|
| [`framework/project-instructions.md`](framework/project-instructions.md) | The project's **custom instructions** | The engine — the grammar, lanes, commit boundary, six-beat arc |
| your filled-in taste file | The project's **knowledge** (uploaded file) | Your signatures and profiles — the thing Claude searches *from* |

Everything else here — the logic doc, the profile format, the examples — is reference
material for you and anyone forking it. None of it needs to reach Claude.

## Before you start

- An **active Splice subscription with credits** on the account you connect.
- A **paid Claude plan** — projects and connectors aren't on the free tier.

## Zero to first download

1. **Enable the Splice connector** in Claude, under Settings → Connectors. Splice's own
   setup guide is the source of truth for the connector URL and login:
   https://splice.com/tools/mcp-server
2. **Create a dedicated Claude project** for this (not just a chat thread — the project
   is what makes your setup persist).
3. **Paste [`framework/project-instructions.md`](framework/project-instructions.md)** into the project's custom instructions.
   That's the engine.
4. **Write your taste file.** Copy [`personal/my-taste.example.md`](personal/my-taste.example.md) to `personal/my-taste.md`
   and fill in one signature and one profile using [`framework/profile-format.md`](framework/profile-format.md). Starting
   from the generic examples in [`examples/profiles/`](examples/profiles/) is fine.
5. **Upload that taste file to the project's knowledge.** This step is what makes your
   profiles visible to Claude — without it you have a well-written file that nothing
   reads. (Pasting the profiles into the custom instructions below the engine works too;
   uploading keeps them easier to revise as calibration sharpens them.)
6. **Run one session.** In that project, tell it what you want — e.g. *"twenty punchy
   kicks"* — and it walks you through the six-beat arc, confirming the exact files and
   credit cost before anything is spent.

New to the flow? **[Walk through a full session](examples/session-walkthrough.md)** — the
six beats end to end, including what the commit boundary actually looks like.

Whenever you revise your taste file, **re-upload it** — the project holds a copy, not a
live link. Same for the engine if you change it.

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

Every one of these choices has a reason behind it, and the reasons are the transferable
part: **[How the curation logic works](framework/curation-logic.md)**.

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

**Do you have post-processing?** Quick test: ask your project to list the files in your
samples folder. If it can read the folder, you have it — turn on renaming, filing, and
the manifest. If it can't, you're on the required core: Splice downloads to its normal
location and you file by hand. The framework degrades gracefully either way; nothing
breaks, you just do the filing yourself.

## Repo layout

```
README.md                     ← you are here
LICENSE                       ← MIT
CONTRIBUTING.md               ← how to contribute (profiles especially welcome)
framework/
  project-instructions.md     ← paste this into your Claude project (the engine)
  curation-logic.md           ← the reasoning, for anyone forking it
  profile-format.md           ← the profile format + a worked example
  glossary.md                 ← one term per concept; the reference docs conform to
  compatibility.md            ← notes on the beta connector
examples/
  session-walkthrough.md      ← a full session, end to end
  profiles/                   ← generic, transferable profile examples
personal/
  my-taste.example.md         ← template for your private taste file
                                 (your filled-in my-taste.md is gitignored — that's why
                                  this folder looks near-empty here)
```

## Licence

MIT — see `LICENSE`. Fork it, improve it, share your profiles back.
