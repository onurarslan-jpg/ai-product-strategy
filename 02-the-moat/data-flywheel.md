# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

**Product:** Sketch To Click Studio — sketch in, deployed full-stack app out.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | **4**/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | **4**/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | **2**/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | **3**/5 |

### Correction Loop - 4/5
**What you capture today:**
The correction signal is captured, not merely generated. Every session produces a
paired before/after with human intent attached — the sketch, the first
generation, the fixes the user made, the version they accepted — and that pairing
is stored in the product's own backend. It is the densest form of training signal
available for this task and it costs nothing to collect, because correcting the
output *is* the workflow.

**How it compounds:**
Corrections feed a shared asset, so a user who never fixed anything still
benefits from fixes made by people before them. That is the point at which a data
advantage starts compounding rather than merely accumulating. It stops short of 5
because 5 means automated retraining — a continuous fine-tune behind evaluation
gates — rather than a shared corpus read back into generation.

### Preference Loop - 4/5
**What you capture today:**
Individual and team preferences accumulate over time and are applied
automatically to new generations. A returning user does not restate their house
style, naming conventions or layout habits; the product already knows them. This
is the loop that makes the tenth sketch a materially different experience from
the first.

**How it compounds:**
Each session sharpens the profile, each sharpened profile raises first-generation
acceptance, and higher acceptance means more sessions. Short of 5 because deep
personalization means conventions learned from one teammate propagating across
the whole team, with measured evidence that acceptance improves as the profile
fills out.

### Domain Context Loop - 2/5
**What you capture today:**
This is the thin one. The substrate for transfer now exists — a shared,
cross-user corrections corpus — but nothing deliberately carries competence from
one domain into an adjacent one. Corrections made on CRM screens are not
systematically mined to improve inventory screens. Whatever transfer does occur
is the foundation model generalising, which every competitor receives on the same
day for the same price.

**How it compounds:**
Weakly, and not by design. This is the cheapest remaining upgrade precisely
because the corpus already exists: the missing piece is a retrieval or
clustering layer over corrections that is domain-aware, not a new data source.

### Network Loop - 3/5
**What you capture today:**
A genuine indirect network effect. Users never interact, but each one's
corrections improve the corpus that serves everyone else, so user five hundred
arrives to a better product than user one did, and leaves it better still.

**How it compounds:**
Quietly and without any social surface — the Waze shape rather than the Slack
shape. It is a 3 rather than a 4 because the benefit is diffuse and unattributed:
there is no shared gallery, no user-contributed templates, no remix graph, and
nothing that makes a user feel the contribution they are making.

**Total Flywheel Score: 13/20**

**Weakest Loop:**
**Domain Context, at 2/5** — and by this framework that is precisely where the
attack lands. The danger is specific: if corrections do not transfer across
domains, then the advantage in any single domain is only as large as the volume
in *that* domain. A corpus spread across ten domains is ten thin corpora, not one
thick one.

**Fix for weakest loop:**
Two routes, and they are strategically opposite, so this is a decision rather
than a backlog item.
- **Concentrate.** Pick one vertical, go deep, and let breadth go. The corpus
  thickens where it is defended and a specialist cannot out-accumulate you on
  your own ground.
- **Transfer.** Build the domain-aware retrieval layer that makes breadth an
  asset: cluster corrections by UI pattern rather than by industry, so a fix made
  on a CRM table improves every table anyone generates afterwards.
The second preserves optionality and is harder; the first is safer and forecloses
a market. Either beats drifting, which is the current path.

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Lovable — the platform this product is built on.
**Vector:** Promote sketch and image input from a supported path to a promoted
entry point. No new capability is required: the project chat already accepts file
attachments, building from a URL already accepts reference images, and there are
three existing routes for importing Figma designs.
**Time-to-threat:** 0-3 months. Arguably already shipped and merely unmarketed.
**% of value at risk:** ~35%. This was the headline risk before the flywheel was
accounted for and it no longer is. They take top-of-funnel, but they cannot
replicate a corrections corpus they cannot see or the personalization built on
top of it. What they capture is first-time users, not returning ones.

### 2. Vertical Competitor
**Attacker:** A domain specialist — a builder that does only internal ops tools,
or only clinical intake, or only field service.
**Vector:** Concentrate every correction into a single domain. They out-accumulate
on the one axis that matters while the generalist's corpus stays spread thin, and
they beat you on your own moat rather than around it.
**Time-to-threat:** 6-12 months.
**% of value at risk:** ~60% of whichever domain they choose. This is now the
primary threat, and it is the direct consequence of Domain Context scoring 2.

### 3. Adjacent Expansion
**Attacker:** Figma via Figma Make; secondarily the general assistants.
**Vector:** Figma owns the surface where sketches already become designs and can
add generate-to-deployed-app inside a workflow that already holds files,
components, comments and handoff. The general assistants arrive by capability
drift rather than intent.
**Time-to-threat:** 6-18 months.
**% of value at risk:** ~30%. They take design-led and casual users; neither
carries the accumulated preference profile that makes a returning user stick.

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*
*(No partner input available — this is the plan I would run against this product.)*

**Attacker:** A vertical specialist, not the platform. The platform attack is
louder but shallower; this one targets the weak loop.

**Attack vector (target the weakest loop):**
Domain Context. Pick the single highest-value domain in the generalist's user
base, build only for it, and make every correction compound into that one
corpus.

**Weeks 1-4 - what they ship:**
A narrow product for one domain, with a domain-specific evaluation set published
openly — the schema conventions, the compliance fields, the layouts that domain
actually uses. Correctness in that domain becomes a measurable, citable claim.

**Weeks 5-8 - how they poach users:**
Run the generalist's own public outputs through the published eval and publish
the gap. The pitch is not "we are faster", it is "we are measurably more correct
for your domain, here is the number" — which is the one claim a thin corpus
cannot answer.

**Weeks 9-12 - why users don't come back:**
Because the specialist's corpus in that domain is now thicker than the
generalist's, and the gap widens with every session. Preference personalization
does not rescue it: a well-learned house style applied to a structurally wrong
schema is still wrong.

**Your defense:**
Decide which of the two fixes above you are running, and run it before the gap is
measurable. Alongside that, start publishing the number that makes the flywheel
visible: first-generation acceptance rate over time, segmented by domain. Right
now the compounding is a claim. Measured and trending, it becomes the thing a
specialist has to beat — and the thing an acquirer or an investor can price.
