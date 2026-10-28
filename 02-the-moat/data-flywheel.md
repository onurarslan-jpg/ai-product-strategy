# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

**Product:** Sketch To Click Studio — sketch in, deployed full-stack app out.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | **1**/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | **1**/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | **1**/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | **1**/5 |

### Correction Loop - 1/5
**What you capture today:**
Nothing, which is the painful part, because the signal is dense and free. Every
session is a correction loop by construction: the user sketches, the model
generates, the user says "no, the table goes above the form" and iterates until
it is right. That produces a labelled before/after pair per session at zero
collection cost. All of it is generated inside the platform's chat and stored in
the platform's project history. This product reads none of it back.

**How it compounds:**
Today it does not compound at all. Of the four loops this has by far the highest
latent value — sketch → first generation → accepted final is exactly the shape
an eval set or a preference-tuning corpus needs — and the lowest cost to start,
since it is a logging decision rather than an ML project.

### Preference Loop - 1/5
**What you capture today:**
Nothing persistent about a person or a team. Every sketch starts cold. The
platform does offer durable preference mechanisms — workspace and project
instructions, design systems, reusable skills, design templates — but those are
hand-authored by the user and live in the platform's workspace, not learned by
this product from watching anyone work.

**How it compounds:**
It does not. A PM's tenth sketch is treated exactly like their first: no learned
house style, no remembered component conventions, no accumulated sense of how
this particular team names things or lays screens out.

### Domain Context Loop - 1/5
**What you capture today:**
Siloed. A sketch for a CRM teaches the product nothing about the next sketch for
an inventory tool. Whatever cross-domain competence shows up is the foundation
model generalising, which every competitor receives on the same day for the same
price. That is borrowed capability, not accumulated advantage.

**How it compounds:**
It does not — and the loop demonstrably exists one level down, where the
platform ships cross-project referencing that reuses code, assets, files and
chat history across a workspace. The mechanism is real; it belongs to the
landlord.

### Network Loop - 1/5
**What you capture today:**
Isolated. No shared library, no public gallery, no user-contributed templates,
no remix graph. User five hundred receives exactly the product user one
received, and contributes nothing to user five hundred and one.

**How it compounds:**
It does not. Again the platform already runs the loop a level below — project
remixing and shared design templates — so the network effect accrues to the
platform while its tenants stay isolated from one another.

**Total Flywheel Score: 4/20**

**Weakest Loop:**
A four-way tie at the floor, so the tiebreak has to be strategic rather than
numerical. Two different answers, and both matter:
- **Fix first: Correction.** It is the cheapest to start, it is already being
  generated for free, and it is the raw input that makes Preference and Domain
  Context buildable later. Nothing else can be built before this one.
- **Most dangerous to lack: Network.** It is the only loop whose absence cannot
  be fixed by effort later — network effects are path-dependent, and the
  platform has a running start on a user base that already includes yours.

**Fix for weakest loop:**
From day one, log every (sketch, first generation, accepted final app, diff
between them) tuple with explicit user consent. No model training required; it
is a logging change measured in days. It moves Correction from 1 to roughly 3
within a sprint, and it is the single asset that survives a pivot if platform
encroachment fires — the generator is replaceable, the labelled corpus is not.

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Lovable — the platform this product is built on.
**Vector:** Promote sketch and image input from a supported path to a
first-class, promoted entry point. No new capability is required: the project
chat already takes file attachments, building from a URL already accepts
reference images, and there are already three routes for importing Figma
designs. What is missing is positioning, not engineering.
**Time-to-threat:** 0-3 months. Arguably already shipped and merely unmarketed.
**% of value at risk:** ~90%. Strip out the input modality and nothing
differentiated remains underneath.

### 2. Vertical Competitor
**Attacker:** Figma, via Figma Make.
**Vector:** They already own the surface where sketches become designs. Adding
generate-to-deployed-app lets them ship this inside a workflow that already
holds the files, component libraries, comments, reviewers and engineering
handoff — the exact depth this product has none of.
**Time-to-threat:** 6-12 months.
**% of value at risk:** ~60%. They take the design-led users and leave behind
only the segment whose input really is a photo of a whiteboard.

### 3. Adjacent Expansion
**Attacker:** OpenAI / Anthropic general assistants.
**Vector:** Capability drift, not strategy. Photograph a sketch in a consumer
assistant, receive a working app with hosting attached. No acquisition, no
integration, no intent to compete in this category specifically.
**Time-to-threat:** 6-18 months.
**% of value at risk:** ~70% of casual and individual use; materially less of
any team or enterprise segment that needs governance, SSO and audit.

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*
*(No partner input available — this is the plan I would run against this product.)*

**Attacker:** Lovable.

**Attack vector (target the weakest loop):**
Attack Network and Correction simultaneously, because the platform already owns
both mechanisms and merely has not pointed them at this use case. Make
sketch-to-app a promoted entry point, then wrap it in a public gallery with
one-click remix so every new sketch improves the next person's starting point —
a compounding loop the tenant cannot answer, since it has no second user to
learn from.

**Weeks 1-4 - what they ship:**
A labelled "Start from a sketch" tile on the project creation screen, pointing
at image attachment that already works. Documentation, a template, a launch
post. Engineering cost close to zero.

**Weeks 5-8 - how they poach users:**
Seed a gallery of sketch-to-app remixes. The obvious seed audience is this
product's own users, because their generated apps, databases and auth already
live on the platform — they are reachable without any migration offer at all.

**Weeks 9-12 - why users don't come back:**
Because there was never anything to come back to. The data, the auth provider,
the storage, the hosting and the project history were always platform-side. The
only thing the tenant ever owned was a sketch upload box, which is now a tile on
the platform's own home screen.

**Your defense:**
Do not defend the input modality; it is already lost. Two things are defensible.
First, the corpus the platform does not bother to assemble — sketch → inferred
schema → human correction, held with consent, paired with an eval harness tuned
to one vertical, which turns a generic generator into a specifically better one
for that vertical. Second, move up the stack into the part the platform has no
interest in: what happens to a generated app *after* it exists — stakeholder
review, versioned decision history, the trail from a whiteboard photo to a
shipped decision. The generator is commodity. The record of why it was built
that way is not.
