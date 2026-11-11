# Profile format

A profile is a named, reusable description of a sound you want, written in plain
language so a search can be composed from it. Profiles are the unit you build up over
time and refine through calibration.

Keep the framework's generic profiles in `examples/profiles/`. Keep *your* profiles —
the ones with your actual taste and any artist references — in your private personal
taste file, out of the public repo.

## Fields

```
Name:           A short handle you'll reuse ("punchy analog kick").
Function:       The category (kick, snare, texture, vocal loop, …).
Signature:      The vibe, in a sentence or two. What it feels like.
Includes:       The positive descriptors that should be present.
Disqualifiers:  What rules a result OUT. Required — a profile without these is too loose.
Constraints:    Optional. BPM range, key, one-shot/loop, duration, dry/wet, acoustic/synthetic.
Transformation: How much the sound affords being changed: high / medium / low.
Good for:       The specific moves it supports — slicing, repitching, granulation, layering.
Default lane:   trusted or review.
Status:         Optional. active (default) or paused — park a category without deleting
                its thinking; note where to route its hits meanwhile.
Notes:          Anything else — references, evolution over time, calibration verdicts.
```

## Guidance

- **Disqualifiers are not optional in practice.** A signature you can't reject against
  can't be triaged. Always say what "too much" looks like.
- **Constraints stay light.** Add them when they help a specific search; don't bake a
  narrow BPM into a profile you'll reuse broadly.
- **Default lane is a starting point, not a rule.** You override it per session.
- **Let the Notes field grow.** This is where calibration verdicts accumulate before
  they get folded into Includes/Disqualifiers.
- **Transformation and Good for are about affordance, not preference.** They answer "what
  could this become?" rather than "do I like it?" A sound you love that affords nothing
  is a worse buy than an unremarkable one you can cut five ways. Splitting affordance out
  from taste stops a strong Includes list from justifying a purchase on its own.
- **Low transformation isn't a strike.** It means the sound arrives ready to use, which
  changes how many you need — a handful of excellent ones, not a category to fill.
- **Split a profile when one category holds distinct sub-kinds,** rather than overloading
  one list. If "breaks" grows into live-drummer, electronic-groove, and hand-percussion
  variants, give them their own profiles (1, 1b, 1c). Profiles can reference each other
  too — "secondary to profile 10," "shares the vocals budget," "route strays to 3 or 9."
- **Pause, don't delete.** When a category stops earning credits for now, set its
  `Status:` to paused with a line on why and where to route its hits — you keep the
  reasoning for when it comes back, instead of rediscovering it.
- **Date your revisions.** A one-line "last refreshed: &lt;date&gt; — &lt;what changed&gt;"
  at the top of your taste file turns it into its own changelog as calibration reshapes it.

## Worked example (generic)

```
Name:           Punchy analog kick
Function:       Kick (one-shot)
Signature:      Tight, weighty, hardware-flavored. Hits once and gets out of the way.
Includes:       Fast transient, controlled low end (roughly 60–90 Hz weight),
                short decay, a little analog grit.
Disqualifiers:  Long boomy tails, sub-only "felt not heard" kicks, over-processed /
                heavily distorted, obviously sample-pack-generic.
Constraints:    one-shot; dry preferred.
Transformation: medium
Good for:       layering, transient replacement, sampler kits
Default lane:   trusted
Notes:          Good candidate for batch approval once a couple of searches confirm the read.
```

See [`examples/profiles/`](../examples/profiles/) for more, and
[`examples/worked-taste-file.md`](../examples/worked-taste-file.md) for a full taste file
built from these fields.
