# Glossary

One term per concept, used the same way in every document here. If you change a term,
change it everywhere — this file is the reference the other docs conform to.

The discipline is borrowed from [ASD-STE100](https://www.asd-ste100.org/) (Simplified
Technical English), which fixes a project's own vocabulary so the same thing is never
called two names. We take that idea and the short-active-sentence habit for the
**engine and procedures**. We deliberately do *not* take its restricted dictionary into
the taste layer — see [Why the taste layer stays unrestricted](#why-the-taste-layer-stays-unrestricted).

---

## Structure

**Engine** — [`framework/project-instructions.md`](project-instructions.md), pasted into a
Claude project's custom instructions. The mechanics. Contains no personal taste.

**Taste file** — your private, filled-in `personal/my-taste.md`, uploaded to the project's
knowledge. Contains all personal taste. Never committed.

**Profile** — a named, reusable description of a sound you want. The unit you build up
and refine. Fields are defined in [`profile-format.md`](profile-format.md).

**Signature** — a named sonic *character* ("dusty & degraded", "loose & pocketed"), stated
as what it includes and what disqualifies it. Profiles reference signatures; signatures
are not tied to one function.

**Function** — what a sound *is*: kick, snare, break, texture, vocal, drone. The only
required search layer.

**Constraint** — an optional operational filter: BPM, key, one-shot vs loop, duration,
dry/wet, acoustic/synthetic.

## Judgment

**Disqualifier** — what rules a result *out*, on a signature or profile. Required. A
profile without disqualifiers cannot be triaged against.

**Global disqualifier** — a disqualifier applied to *every* search, above per-profile
rules. Collectively, the **anti-library**: the standing description of what you never
want to spend credits on.

**Collection test** — the questions a candidate must pass to be worth a credit, beyond
matching a profile. Guards against buying things that match on paper but earn nothing.

**Transformation read** — how much a sound affords being changed (high / medium / low).
Weighs *usefulness as raw material*, separately from whether you like it as-is.

## Session

**Beat** — one of the six stages of a session: Intent → Search translation → Triage →
Audition/approval → Download & filing → Calibration. Always "beat", never "step" or
"stage".

**Lane** — how much review a search gets. **Trusted** = eligible for batch approval after
a quick scan. **Review** = every candidate auditioned individually. Trusted is
*low*-review, never *no*-review. Chosen per search.

**Triage** — sorting candidates on metadata and descriptions into likely-yes, maybe, and
ruled-out. Done by Claude, on text only — never on sound.

**Commit boundary** — the mandatory confirmation before any credit is spent: exact
filenames, exact count, exact credit cost, explicit go. Applies in both lanes, always.

**Calibration** — the closing beat. Lightweight verdicts on what was downloaded, folded
periodically back into signatures and profiles.

## Filing

**Required core** — what works on the connector alone: search → review → approve →
download.

**Optional post-processing** — rename → organize → deduplicate → manifest. Depends on
your Claude environment's filesystem access. Never promised when unavailable.

**Manifest** — the running record of each download (source ID, filename, intent, credits,
date, destination). Doubles as the deduplication backbone.

**Yield** — downloaded ÷ reviewed, for one session. **Retention** — still useful at a
later library review. Both optional sanity checks, never targets.

---

## Why the taste layer stays unrestricted

A controlled vocabulary is the right tool when ambiguity is the enemy — a maintenance
procedure must have exactly one reading. The engine benefits from that: short sentences,
active voice, one term per concept, no metaphor.

The taste layer is the opposite case. Its whole functional payload is connotation.
"Busy without pocket", "beautiful but inert", "leaves somewhere to go" do precise triage
work that no restricted-dictionary paraphrase can reproduce — and the reader is a
language model doing semantic retrieval against a sample catalog, where rich descriptors
are signal rather than noise. Flattening them costs search quality directly.

So: discipline the mechanics, leave the ears alone.
