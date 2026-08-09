# How the curation logic works

This explains the *why* behind the framework so you can improve it intelligently
rather than just copy it. If you're going to fork it, read this first.

## The problem it solves

Splice's download experience is one-at-a-time and slow. If you've accumulated a large
credit balance, spending it down means either grinding through samples individually
(hours) or dumping whole packs (300 samples, most of which you'll never use). Neither
respects the fact that the credits are finite and the point is a *good* library, not a
big one.

Splice's official MCP connector changes the mechanics: you can search by natural
language, audition, and download with credits, all inside a Claude conversation. That
removes the click-by-click grind. But raw speed just relocates the problem — now you can
accumulate junk faster. The framework exists to keep speed and selectivity at the same
time.

## The one idea everything hangs on

**Human taste, accelerated mechanics.** The scarce thing is judgment — your ears
deciding what's worth keeping. Everything else (searching, sorting, tracking, filing)
is mechanical and can be accelerated. The whole design keeps those two separated so
speed never eats selectivity.

That's also why there's no app and no autonomous agent here. An app would re-implement
what the connector already gives you for free. Agents parallelize work that has no human
in the loop — the opposite of this, where the human *is* the loop.

## Why three layers, not two

Taste alone (function + vibe) gets you close, but real production searches also carry
operational needs: tempo, key, one-shot vs loop, dry vs wet. Making those a third,
*optional* layer keeps the taste model clean while still letting you get specific when
it matters. Optional is the key word — over-constraining returns thin, obvious results
and kills discovery. The grammar is something you reach into, not a form you fill.

## Why signatures carry disqualifiers

A vibe defined only by what it includes is too loose to triage against. "Dusty" that
also says *what it rules out* (too clean, too glossy, too modern) gives the triage step
something to reject on. Negative preferences are what make a signature usable, not just
evocative.

## Why "trusted" means low-review, not no-review

The failure mode this framework is built to prevent is quietly becoming the bulk-dump it
replaced. A "just grab these ten" lane is efficient, but if it becomes no-review it's
the same indiscriminate accumulation with extra steps. So trusted means *eligible for
batch approval after a quick scan* — the review is lighter, never absent. And regardless
of lane, one hard commit boundary (exact files, count, credit cost, explicit go) means
nothing spends a credit just for showing up in results.

## Why calibration is the most reusable part

A taste file written once is frozen at your first guess. The calibration beat — a few
lightweight verdicts after each session, periodically folded back into the signatures —
is what makes the profiles converge on your actual taste over time. If you take one idea
from this project into something else, take this one: a curation system that doesn't
learn from its own verdicts stays as good as its first draft forever.

## Why filing is split

Downloading is guaranteed by the connector. Renaming, organizing, deduplicating, and
manifesting depend on the specific Claude environment's filesystem access, which varies.
Splitting the workflow into a **required core** (search → review → approve → download)
and **optional post-processing** keeps the framework honest: it never promises local
file behavior the connector alone can't deliver, and it degrades gracefully where that
behavior isn't available.
