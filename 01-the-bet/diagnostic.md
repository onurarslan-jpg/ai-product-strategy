# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** Sketch To Click Studio — upload a hand-drawn sketch or whiteboard
photo of a screen, get back a clickable, navigable prototype.
**Your Role:** Product Manager

---

## Scores

**Scoring direction:** 5 = strongest position, 1 = most vulnerable, on all three
axes. So *Platform Exposure 1* means heavily exposed, not well defended. This
reading is what makes the calibration note work — if everything is a 5, the
diagnostic hasn't bitten.

### Contextual Moat — 1/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:**
They would leave in an afternoon, not a weekend. The product is one stateless
step: sketch in, prototype out. There is no account, no saved project, no
version history, no component library, no team conventions, no comment threads,
no handoff to engineering. Nothing accumulates, so nothing has to be migrated —
the switching cost is the time it takes to open a different tab. Against the
calibration given (Figma = deep moat, thin ChatGPT wrapper = shallow), this sits
at the shallow end: Figma's depth is the files, libraries and collaboration
history around the canvas, and none of that exists here.

**Named attacker (from partner challenge):**
**Figma.** They already own the surface where sketches become designs, Figma
Make already generates working UI, and they would ship sketch-to-prototype
inside a workflow that already holds the user's files, components and reviewers.

### Data Advantage — 2/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:**
There is a genuinely proprietary signal available here, which is why this is a 2
and not a 1: the pairing of a sketch with the prototype the user *accepted*, plus
every correction they made afterwards. That is a preference-and-eval dataset for
a narrow task, and OpenAI does not see it. But it is latent, not held — nothing
captures it today, volume is zero, and the underlying task sits close enough to
general image-to-code that foundation models keep improving at it without any
contribution from this product. An asset you have identified but not yet
collected is worth 2 at most.

**Named attacker (from partner challenge):**
**OpenAI / Anthropic**, whose general multimodal models raise the floor on
image-to-code for everyone at once. Closer to home, **Lovable** observes vastly
more prompt → app → edit cycles than this product ever will.

### Platform Exposure — 1/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:**
The hero feature is one capability away from being a checkbox in somebody else's
product, and several vendors are already most of the way there: Claude and
ChatGPT will take a photo of a sketch and emit working code today. The sharpest
version of the risk is that this product is built *on* Lovable, so the platform
it depends on is also the competitor best placed to absorb it. Pivot speed is
the one bright spot — it is a thin, young product and could be repointed in
days — but there is very little to pivot with, since neither moat nor dataset
has accumulated.

**Named attacker (from partner challenge):**
**Lovable** — the platform this runs on, which can absorb sketch input as a
feature without acquiring anything.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
The input format *is* the entire product, and the platform it is built on can
ship that input format as a feature before any moat or dataset accumulates.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
**L.** The load-bearing assumption — that a sketch beats a typed description as
input — has not been tested, and the deployed build does not currently serve the
prototype at all. Kill criterion 1 is the cheapest way to move this to M or H,
and it should run before anything else is built.
