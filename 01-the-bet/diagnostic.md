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
axes. So *Platform Exposure 1* means heavily exposed, not well defended.

### Contextual Moat — 2/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:**
Because the output is a deployed application rather than a mock, real state
accumulates: user accounts, rows in Postgres, uploaded files, a schema someone
has since hand-edited, a URL other people already use. That is a genuine
switching cost, and it is why this is not a 1.

What caps it at 2 is who the switching cost belongs to. Every durable asset —
the database, the auth provider, the storage bucket, the hosting — lives in the
platform's backend, not in this product. The sketch-to-app step is still one
stateless hop at the front of someone else's stack. Worse, the platform
deliberately engineers exit: it documents full database export, daily backups,
code download and two-way Git sync, and markets one-click import *from* Replit,
Bolt, v0 and Base44 including their databases and users. A user who wants to
leave takes their app with them in an afternoon, by design.

**Named attacker (from partner challenge):**
**Figma.** They own the surface where sketches already become designs, Figma
Make already generates working UI, and the depth they hold — files, component
libraries, comments, reviewers, handoff — is exactly the layer this product
lacks.

### Data Advantage — 2/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:**
Full-stack output raises the ceiling here considerably. The signal is no longer
just sketch → accepted UI; it is sketch → inferred data model → auth choices →
whatever the human corrected afterwards. Which tables a person implied when they
drew three boxes and an arrow is genuinely rare training signal, and it is not
in any public corpus.

The floor has not moved, which is why the score has not either. None of it is
captured today, volume is zero, and the platform underneath observes the same
prompt → app → correction loop across every project on it, at a scale this
product will never reach. The asset is identified, not held — and the party best
placed to hold it is the platform, not its tenant.

**Named attacker (from partner challenge):**
**Lovable**, which sees the identical signal across its whole user base.
Secondarily **OpenAI / Anthropic**, whose general multimodal models lift
image-to-code for everyone without needing anyone's proprietary pairs.

### Platform Exposure — 1/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:**
Understanding the platform properly makes this score worse, not better. The
differentiator is the input modality — a sketch instead of a sentence — and the
platform already ships it. Its project chat accepts file attachments, it
documents building from a URL *with reference images*, and it offers three
separate routes for importing Figma designs. The hero feature is not one
checkbox away; it is already present as a supported path.

That leaves this product as a narrower entry point into a platform that performs
the entire remaining job, while depending on that platform for the job itself.
The usual consolation — fast pivot — does not help much, because after removing
the sketch step there is nothing underneath that is not the platform's.

**Named attacker (from partner challenge):**
**Lovable** — the platform this is built on, which already accepts image input,
already generates the full stack, and has made absorbing adjacent tools
(Replit, Bolt, v0, Base44) an explicit product strategy.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
Every durable asset the product creates — accounts, data, deployment, telemetry
— accrues to the platform it is built on, while the one thing that is genuinely
its own, sketch-as-input, is already a shipped platform feature.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
**L**, and lower than before the platform's capabilities were understood
properly. The load-bearing assumption is no longer "can AI turn a sketch into an
app" — the platform answers that — but "is a sketch a better entry point than
pasting the same image into the platform's own chat." That has not been tested,
and it is cheap to test. Kill criterion 1 should run before anything else is
built.
