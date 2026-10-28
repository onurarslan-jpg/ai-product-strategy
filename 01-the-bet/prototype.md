# The Prototype Bet

## What I Built
<!-- One sentence: what does this prototype demonstrate? -->
A studio that turns a hand-drawn sketch or whiteboard photo of a screen into a
clickable, navigable prototype in one step — upload the sketch, get working
screens you can click through.

## Tool Used
<!-- v0 / Cursor / Lovable / other -->
Lovable

## Prototype Link
<!-- Paste the shareable URL -->
https://sketch-to-click-studio.lovable.app/

## AI Value Archetype
<!-- Automator / Copilot / Oracle / Creator / Orchestrator -->
**Creator** — it generates a new artifact from a rough input. Not Automator
(no existing workflow is being removed), not Copilot (it doesn't work alongside
you), not Oracle (it produces an object, not an answer), not Orchestrator
(one model, one step).

## The Bet in One Sentence
<!-- What you're building, for whom, why now -->
For product managers who can sketch an idea but can't build one, Sketch To Click
Studio turns a whiteboard photo into a clickable prototype in under a minute —
worth betting on now because image-to-code models have only just cleared the
fidelity bar where output is testable with real users instead of merely pretty.

## Kill Criteria
<!-- When would you stop? What evidence would kill this bet? -->
Each criterion kills a different load-bearing assumption. Every one has a
threshold and an expiry date — a criterion with no date never fires.

**1 · Sketch input earns its place** — *gate: 11 Nov 2026*
The bet dies here first, so test it first. Run 10 ideas twice: once from a
sketch, once from a two-sentence text description into the same model. Blind
reviewers pick which output better matches intent.
**Kill if** the sketch arm wins under 65% of pairs. Below that, sketching is
ceremony and this is a thin wrapper on Lovable.

**2 · Output is usable unedited** — *gate: 11 Nov 2026*
10 PMs each upload one real sketch from work they are actually doing.
**Kill if** fewer than 6 of 10 first-generation outputs get used in a real
stakeholder review or user test with no manual editing. Measured by what they
did, not what they said they would do.

**3 · People come back** — *gate: 9 Dec 2026*
**Kill if** fewer than 3 of the first 20 activated users upload a second sketch
within 14 days of their first. One-and-done is a demo, not a tool, and second
use is the cheapest honest demand signal available.

**4 · The unit economics survive** — *gate: 9 Dec 2026*
**Kill if** median cost per accepted prototype (inference plus retries) exceeds
€2 while under 20% of surveyed PMs say they would pay €20/month. Either number
alone is survivable; together they are not.

**5 · Platform encroachment** — *pivot trigger, watch to 31 Jan 2027*
**Stop or pivot if** Figma, Lovable, v0 or an OS vendor ships sketch-to-prototype
as a native first-class feature that clears criterion 2's bar. This is a pivot
trigger rather than a kill: the asset worth keeping would be the evaluation
harness, not the generator.

**Review cadence:** criteria 1–2 are checked on 11 Nov 2026, criteria 3–4 on
9 Dec 2026. Thresholds may be revised *before* a gate opens, never after
the result is known.
