# The Prototype Bet

## What I Built
<!-- One sentence: what does this prototype demonstrate? -->
A studio that turns a hand-drawn sketch or whiteboard photo of a screen into a
working full-stack application — generated UI wired to a real database, with
authentication, storage and a live deployed URL, not a disposable clickable mock.

## Tool Used
<!-- v0 / Cursor / Lovable / other -->
Lovable

## Prototype Link
<!-- Paste the shareable URL -->
https://sketch-to-click-studio.lovable.app/

## AI Value Archetype
<!-- Automator / Copilot / Oracle / Creator / Orchestrator -->
**Creator** — it generates a new artifact from a rough input, and the artifact
is a running application rather than a picture of one. Not Automator (no
existing workflow is being removed), not Copilot (it doesn't work alongside
you), not Oracle (it produces a system, not an answer), not Orchestrator
(one generative step, not a coordinated chain).

## The Bet in One Sentence
<!-- What you're building, for whom, why now -->
For product managers who can draw the thing they want but cannot build it,
Sketch To Click Studio turns a whiteboard photo into a deployed, data-backed
application in minutes — worth betting on now because full-stack generation has
become a commodity, which moves the open question from *can it be built* to
*what is the fastest honest way to express intent*.

## Kill Criteria
<!-- When would you stop? What evidence would kill this bet? -->
Each criterion kills a different load-bearing assumption. Every one has a
threshold and an expiry date — a criterion with no date never fires.

**1 · Sketch beats the platform's own image input** — *gate: 11 Nov 2026*
The bet dies here first, so test it first, and test it against the right
control. The comparison is not sketch versus typed description; the platform
already accepts image attachments, builds from a URL with reference images, and
imports Figma files. Run 10 ideas three ways: (a) sketch through this studio,
(b) the same sketch pasted straight into the platform's own chat, (c) a
two-sentence text description. Blind reviewers rank the outputs against intent.
**Kill if** (a) fails to beat (b) on at least 65% of pairs. Losing to (c) is
embarrassing; losing to (b) means there is no product.

**2 · Output is usable unedited** — *gate: 11 Nov 2026*
10 PMs each upload one real sketch from work they are actually doing.
**Kill if** fewer than 6 of 10 first-generation apps get used in a real
stakeholder review or user test with no manual editing. Measured by what they
did, not what they said they would do.

**3 · People come back** — *gate: 9 Dec 2026*
**Kill if** fewer than 3 of the first 20 activated users upload a second sketch
within 14 days of their first. One-and-done is a demo, not a tool, and second
use is the cheapest honest demand signal available.

**4 · The unit economics survive** — *gate: 9 Dec 2026*
**Kill if** median cost per accepted app (generation plus retries plus hosting
and backend credits) exceeds €2 while under 20% of surveyed PMs say they would
pay €20/month. Either number alone is survivable; together they are not.

**5 · Platform encroachment** — *pivot trigger, watch to 31 Jan 2027*
**Stop or pivot if** the underlying platform, Figma, v0 or an OS vendor makes
sketch-to-app a first-class, promoted path that clears criterion 2's bar. This
is a pivot trigger rather than a kill: the asset worth keeping would be the
sketch → schema → correction dataset and the evaluation harness, not the
generator.

**Review cadence:** criteria 1–2 are checked on 11 Nov 2026, criteria 3–4 on
9 Dec 2026. Thresholds may be revised *before* a gate opens, never after
the result is known.
