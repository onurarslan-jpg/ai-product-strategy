# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** Sketch To Click Studio — upload a hand-drawn sketch or whiteboard
photo of a screen and get back a working full-stack application: generated UI
backed by a real database, authentication, storage and deployment, not a
disposable clickable mock.
**Your Role:** Product Manager
**Competitive position:** General-purpose AI creator platform. The peer set is
other horizontal builders; the threat set is domain specialists.

---

## Scores

**Scoring direction:** 5 = strongest position, 1 = most vulnerable, on all three
axes. So *Platform Exposure 2* means heavily exposed, not well defended.

### Contextual Moat — 3/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:**
The real switching cost is the accumulated preference profile. A returning team
does not restate its house style, naming conventions or layout habits, because
the product already knows them; leaving means a cold start, and that cost grows
with every session rather than staying flat. Underneath it sits the generated
application — accounts, rows, files, a live URL — which is a second, smaller
anchor.

What caps it at 3 is the absence of the one switching cost that actually holds
creators: an audience. A specialist platform that hands a creator players is
offering something a preference profile cannot match, because leaving costs them
their users rather than their settings. Generated artifacts are also exportable
by design — code download, database export, standard stacks — so the artifact
anchor is weaker than it looks.

**Named attacker (from partner challenge):**
**Astrocade.** Creators come for the builder and stay for the catalogue and its
play counts. That is a switching cost denominated in audience, which no amount
of personalization answers.

### Data Advantage — 3/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:**
Still the axis the bet rests on, but scored down from 4 after the M2 breakout
exposed a blind spot. Every editor session yields a paired before/after with
human intent attached - sketch, first generation, corrections, accepted result -
captured in our own backend and shared across users. Dense, free to collect, and
genuinely unavailable elsewhere.

The corpus stops at the editor boundary, though. Failures after deployment - a
checkout leak, an exposed row, an edge function failing under load - never reach
it. So the advantage is real on *intent* and absent on *outcome*: we learn what
people approve of, not what works. That is the gap a specialist grading on
production outcomes attacks, and it is why this is a 3.

The fix is unusually cheap for a gap this size, because we host the apps and
already collect their runtime logs. The outcome label exists; it is not yet
joined back to generation.

**Named attacker (from partner challenge):**
**A vertical specialist that instruments production** - in my partner's words,
"Lovable learns whether code looks acceptable and as a competitor I would learn
whether it succeeds."

### Platform Exposure — 2/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:**
As a horizontal creator platform, the exposure is to the model layer rather than
to a landlord. General assistants already accept a photograph of a sketch and
return working code, and each capability release narrows the gap between this
product and a general-purpose chat window — without any intent to compete in this
category specifically.

The exposure is a 2 rather than a 1 because what is at risk is acquisition rather
than retention: a general assistant takes first-time users but cannot replicate a
corrections corpus it cannot see or the personalization built on it. It is a 2
rather than a 3 because the defence is thin in the direction that matters — the
product's differentiation sits in the generation step, which is precisely the
layer commoditising fastest.

**Named attacker (from partner challenge):**
**OpenAI / Anthropic.** Encroachment by capability drift, not by strategy, which
makes it impossible to negotiate with and pointless to out-feature.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
The product learns from acceptance inside the editor while a specialist learns
from outcomes after deployment — so in any vertical it chooses, the specialist
out-learns a corpus that is both thinner and graded on a weaker label, and holds
its creators with an audience rather than a settings file.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
**M.** The question that mattered — is there an asset here that compounds — is
answered yes. Three things keep it off H: the compounding is claimed rather than
measured, the corpus is indexed by vertical rather than by pattern and graded on
a weak label, and there is no distribution loop, which is the switching cost a
specialist will compete on. The first is a dashboard, the second is a re-index,
the third is a strategy decision.
