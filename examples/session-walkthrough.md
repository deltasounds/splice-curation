# A session, end to end

An illustrative run through the six beats, so you can see the shape before your first
one. **The filenames, counts, and pack names below are invented for illustration** —
they're not real Splice results. What's accurate is the *structure*: who speaks when,
where the decisions sit, and what the commit boundary looks like in practice.

The session: twenty punchy kicks, using the `punchy-analog-kick` profile from
`examples/profiles/`.

---

## Beat 1 — Intent

> **You:** Twenty punchy kicks. Use my punchy analog kick profile.

That's the whole beat. Function (kick, one-shot) and Signature (punchy analog) come from
the profile; you didn't need to restate them. No constraints — you're searching loose on
purpose.

## Beat 2 — Search translation

> **Claude:** Reading from **Punchy analog kick**: fast transient, controlled 60–90 Hz
> weight, short decay, a little analog grit. Ruling out long boomy tails, sub-only kicks,
> heavily distorted, generic-pack-sounding.
>
> Searching one-shots (a real filter), with "dry, short decay" written into the
> description — Splice can't filter on those, so I'll check them against the tags at
> triage. The profile's default lane is **trusted**, so I'll mark each result rather
> than making you audition all forty. Want to keep it trusted, or switch to review?
>
> **You:** Trusted is fine.

Claude confirms the read *before* spending a search. If it had misread the profile, this
is where you'd catch it — cheaply.

## Beat 3 — Triage

> **Claude:** Forty results, all shown in Splice's order, each marked:
>
> 1. `ANALOG_KICK_017.wav` — **likely-yes**: "tight, punchy, tape-saturated", 0.4s
> 2. `deep_kick_808_G.wav` — **maybe**: 1.8s decay. Long for the profile; could be the
>    boomy tail you rule out, or usable trimmed.
> 3. `sub_boom_44.wav` — **ruled-out**: tagged "sub-only" (profile disqualifier)
> 4. `kick_drive_C.wav` — **likely-yes**: "short decay, driven analog", 0.3s
> 5. `kick_processed_02.wav` — **maybe**: "heavily saturated". Right family, possibly
>    past your distortion line.
> 6. `trap_808_long.wav` — **ruled-out**: explicitly "trap 808", 2.4s tail
> - … (through 40)
>
> Totals: 14 likely-yes, 9 maybe, 17 ruled-out. Each has a Splice link to listen.

Note what Claude is and isn't doing. Splice requires every result to be shown in order,
so nothing is hidden: ruled-out items stay on the list with their reason, which keeps the
disqualifiers visible and correctable. Claude is reading *descriptions, tags and duration*
against your disqualifiers. It has not heard any of these. The maybes exist precisely
because metadata can't settle those calls.

## Beat 4 — Audition / approval

You audition the nine maybes in Splice. Three are keepers.

> **You:** Take all 14 likely-yes. From the maybes, `deep_kick_808_G` and
> `kick_processed_02` are out — both too much. `kick_room_A`, `kick_vintage_D`,
> and `kick_tape_11` are in.

Seventeen approved. You never auditioned the fourteen — that's what the trusted lane
buys you, and why the profile's disqualifiers have to be sharp enough to trust.

## Beat 5 — The commit boundary, then download

> **Claude:** Before anything is spent:
>
> **17 files, 17 credits.**
>
> ```
> ANALOG_KICK_017.wav        kick_drive_C.wav
> kick_room_A.wav            kick_vintage_D.wav
> kick_tape_11.wav           … (12 more)
> ```
>
> One flag: `kick_drive_C.wav` is already in your manifest from the March 3 session.
> Re-downloading is free, so it wouldn't cost a credit — but you already have it.
> Dropping it puts you at **16 files, 16 credits.**
>
> Go?
>
> **You:** Go.

This is the beat that makes the whole thing safe. Exact filenames, exact count, exact
cost, and an explicit yes — every time, trusted lane included. Nothing about a result
appearing in a list spends a credit.

Then Splice downloads. Each download comes back as a link that expires quickly. If your
environment can save files to your computer, filing follows: saved, renamed, sorted into
`kicks/analog/`, manifest updated. If it can't, Claude shows every link at once next to
its filename so you can grab them before they expire, plus the manifest rows to paste
in. You file by hand, and the session is still complete.

## Beat 6 — Calibration

> **Claude:** Quick verdicts while it's fresh?
>
> **You:** `kick_room_A` — yes, the room sound is exactly it. `kick_tape_11` — no, too
> soft on the transient. Two of the trusted 14 were flat-sounding, both from the same
> pack.

Seconds, not a form. Later, when "too soft on the transient" has come up three or four
times, it gets folded into the profile's **Disqualifiers** — and the next search returns
fewer of them. That compounding is the point of the whole system; the downloads are just
this session's output.

---

## What to notice

- **Confirmation before searching** (beat 2) is cheap; a bad search is not.
- **The maybe pile is where you actually work.** A profile with vague disqualifiers makes
  it huge; a sharp one makes it small.
- **The commit boundary never bends** — not for a trusted lane, not for a small batch.
- **Deduplication needs the manifest.** Without post-processing you're tracking that
  yourself, which is a real reason to check whether your environment supports it.
- **Calibration is the compounding step**, and the easiest one to skip. Don't.
