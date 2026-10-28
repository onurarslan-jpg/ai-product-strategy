# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** Sketch To Click Studio — upload a hand-drawn sketch or whiteboard
photo of a screen and get back a working full-stack application: generated UI
backed by a real database, authentication, storage and deployment, not a
disposable clickable mock.
**Your Role:** Product Manager

---

## Scores

**Scoring direction:** 5 = strongest position, 1 = most vulnerable, on all three
axes. So *Platform Exposure 2* means heavily exposed, not well defended.

### Contextual Moat — 3/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:**
Two distinct switching costs stack here. The first is the deployed application
itself: accounts, rows in Postgres, uploaded files, a URL other people already
use. The second, and the one that actually holds users, is the accumulated
preference profile — a returning team does not restate its house style, naming
conventions or layout habits, because the product already knows them. Leaving
means going back to a cold start, and that cost grows with every session rather
than staying flat.

What caps it at 3 is that the infrastructure layer remains the platform's, and
the platform deliberately engineers exit: documented database export, daily
backups, code download, two-way Git sync, and one-click import *from* competing
tools. A user can take the artifact with them in an afternoon. What they cannot
take is the learned profile and the shared corrections corpus — which is exactly
why the moat sits at 3 rather than 1 or 5.

**Named attacker (from partner challenge):**
**Figma.** They own the surface where sketches already become designs, and the
depth they hold — files, component libraries, comments, reviewers, handoff — is
the one layer this product still lacks.

### Data Advantage — 4/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:**
This is the strongest axis and the reason the overall bet is live. Every session
produces a paired before/after with human intent attached: the sketch, the first
generation, the corrections, the accepted result. That pairing is captured in the
product's own backend and fed into a shared asset, so a user who never corrected
anything still benefits from corrections made before they arrived. The signal is
dense, free to collect — correcting the output *is* the workflow — and genuinely
unavailable elsewhere. Which tables a person implied when they drew three boxes
and an arrow is in no public corpus, and OpenAI does not see it.

It is a 4 rather than a 5 because the compounding is asserted rather than
measured, and because the corpus is spread across domains rather than
concentrated in one. A thick corpus in one domain beats a thin corpus in ten;
first-generation acceptance rate over time, segmented by domain, is the number
that would settle this.

**Named attacker (from partner challenge):**
**A vertical specialist** that concentrates every correction into a single
domain and out-accumulates on the one axis that matters. Not the platform — it
cannot see inside this product's database.

### Platform Exposure — 2/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:**
The encroachment risk on the input modality is real and close to immediate: the
platform already accepts image attachments, already builds from a URL with
reference images, and already imports Figma designs three ways. Sketch-as-input
is not a defensible feature and should not be treated as one.

What has changed is how much that costs. Shipping a sketch tile takes the
platform top-of-funnel; it does not take returning users, because it cannot
replicate a corrections corpus it cannot see or the personalization built on it.
The exposure is a 2 rather than a 1 because the thing at risk is now acquisition
rather than retention — and a 2 rather than a 3 because the dependency underneath
is still total: hosting, auth, database and deployment all belong to the same
company best placed to encroach.

**Named attacker (from partner challenge):**
**Lovable**, which already ships every input path this product differentiates on
and has made absorbing adjacent tools an explicit strategy.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
The flywheel is real but domain-thin: corrections do not transfer between
domains, so a vertical specialist can out-accumulate the corpus inside any single
domain while the generalist's advantage stays spread too thin to defend.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
**M.** The question that mattered — is there an asset here that compounds — is
answered, and the answer is yes. Three things keep it off H: the compounding is
claimed rather than measured, the domain-thinness above is unaddressed and is now
the primary attack surface, and the deployed build does not currently serve the
product. The first is a dashboard, the second is a strategy decision, the third
is a bug.
