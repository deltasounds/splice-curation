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

## Why there's an anti-library

Per-profile disqualifiers only fire once a profile is in play. But most wasted credits go
to things that match *some* profile loosely and shouldn't have been considered at all —
finished construction kits, generic genre presets, another two hundred near-identical
808s. So the taste file carries **global disqualifiers** that apply above every search.

The sharpest test for what belongs there: **don't spend credits on what your gear already
makes.** If you own a capable synth, polished synth loops are a bad buy at any quality —
not because they're bad, but because you can produce them and you can't produce someone
else's room, tape machine, or drummer. The anti-library is where that reasoning gets
written down once instead of being re-litigated every session.

## Why affordance is scored separately from taste

A profile that only describes what you like will approve sounds you can't do anything
with. Rating each profile for **transformation** (how much it affords being changed) and
**what it's good for** (which specific moves) forces the second question every time.

This matters most in the trusted lane, where liking the description is doing a lot of
work. A gorgeous finished loop and a strange unusable fragment can both score well on
Includes; only one of them earns a credit in a library of *ingredients*. Splitting the
two also tells you how much to buy: high-transformation material rewards volume, because
each piece has many futures. Low-transformation material arrives finished, so a handful
is the whole category.

## Why contrast is protected explicitly

A well-tuned signature has a monoculture problem. Sharpen "dusty and degraded" enough and
every search returns the same sound, the library converges, and everything made from it
sounds identical. The disqualifiers work perfectly and the result is worse.

So the framework treats **contrast as a thing to defend**, not an accident to tolerate.
Clean, precise, pristine material earns its place when it has distinctive character;
degradation is available downstream and doesn't need buying. The useful territory is
usually a collision — organic against synthetic, precise against loose, beautiful against
abrasive — and a library with only one pole can't produce one.

## Why there's always a wildcard

Every taxonomy has the same blind spot: **it can only find what you already imagined.**
A profile set is a description of your taste as of the day you wrote it, and searching
strictly within it guarantees you never encounter the thing that would have changed it.

The fix is a deliberately underspecified profile — sounds whose use isn't obvious, kept
in the review lane, at low volume. Low volume is the load-bearing part. Without a cap,
"it's interesting" becomes the excuse that reopens indiscriminate accumulation from the
other direction. Curiosity is the entry test, and it's the human's to apply — Claude
cannot run it.

## Why matching a profile isn't sufficient

Profiles filter; they don't decide. A candidate can satisfy Includes, dodge every
disqualifier, and still be a poor use of a finite credit. A **collection test** — a small
fixed set of questions applied on top of the profile match — catches that: does it contain
something distinctive to work with, does it leave you room rather than finishing the job,
does it make you curious?

The second question is the one that does unexpected work. Finished, resolved, complete
material is the easiest thing to approve and the hardest to use, because there's nowhere
left to go. Incomplete propositions beat finished ones in a library meant to be
transformed.

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
