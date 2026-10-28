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
The data exists; it is filed in the wrong shape. A correction made on a CRM
contact screen - status should be an enum rather than free text, filter above the
table rather than beside it - is not a lesson about CRMs. It is a lesson about
filterable tables, and it applies unchanged to a support queue, an inventory
list, an applicant tracker. Filed by industry it stays locked in "CRM". The
transferable unit is the UI and schema pattern, not the vertical.

**How it compounds:**
Weakly, and the arithmetic is unforgiving. A thousand corrections spread over ten
domains behave like a hundred each. Indexed by pattern, where the overlap between
domains is heavy, the same thousand corrections might represent roughly twice as
many applicable lessons. This loop is the multiplier on every other loop's
output, which is why leaving it at 2/5 wastes the asset the other three scores
depend on.

**The signal that it is failing:** correction recurrence - are users making the
same fix repeatedly across sessions? If they are, the corpus is not being read
back, and that shows up well before any quality gap becomes externally visible.
Pair it with first-generation acceptance segmented by domain: wide variance means
thin everywhere rather than strong on average.

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
**Attacker:** A domain-specialist creator platform. The live example is
**Astrocade** (astrocade.com) — AI-built casual mobile games.
**Vector:** They do not compete on generation quality, they compete on three
things a generalist structurally lacks. Their catalogue is indexed by genre —
Platformer, Arcade, Merge, Horror, Incremental — which is a pattern index, so
corrections cluster where they transfer. Their feedback label is plays, not
acceptance: a game showing 3.2M plays against one showing 29 is graded by
outcome, where a generalist only ever learns that someone clicked accept. And
their Astro Academy codifies the craft — core mechanics, game feel, first
impression, download time — turning tacit domain knowledge into curriculum that
both teaches creators and standardises what "good" means inside the corpus.
**Time-to-threat:** Already live in their vertical. 6-12 months for the pattern
to be copied into a second one.
**% of value at risk:** ~60% of whichever vertical is targeted. This is now the
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

*Captured from the breakout. The attacker below is the most dangerous plan, not
the most likely one - the likely version is the domain specialist in threat 2
above. This is the same attack with distribution and planetary-scale outcome data
attached.*

**Attacker:** Head of Product, Google - Developer Ecosystem.

**Attack vector (target the weakest loop):**
Domain Context, 2/5. Not generation quality - that would take them a year to
catch. They come at the fact that corrections are filed by industry and graded on
whether someone clicked accept.

**Weeks 1-4 - what they ship:**
Sketch-to-app inside their existing developer tooling, free tier, no new model
research required. The difference is the scaffold: every generated app is
conditioned on what actually retains in its store category. They already own the
index - a category taxonomy fifteen years old, with retention, install
conversion, crash-free rate and ARPU sitting behind every category. They do not
need to build a domain-context loop, only point an existing one at generation.

**Weeks 5-8 - how they poach users:**
Two offers a generalist cannot match. Before a creator ships, show them projected
D1 retention and install conversion against the category median. After they ship,
one-click store listing - a ranking, a review surface and an audience on day one,
where we hand back a URL and nothing else. Migration runs on our own tooling:
code download, database export and two-way Git sync are their import pipeline.

**Weeks 9-12 - why users don't come back:**
Their loop closes on outcomes, ours on intentions. Every week their generator
gets better at retention while ours gets better at looking approvable, and by day
90 the gap is measurable in the only metric a creator is judged on. By then the
creator's users, ratings and ranking live there. Leaving them costs an audience;
leaving us costs a settings file.

**Your defense:**
1. **Change what we are graded on.** Acceptance is a proxy for quality, not
   quality. Any outcome signal from deployed apps - usage, retention, whether the
   app is still running after 30 days - beats it, and it is observable without
   asking anyone. This is the only move that attacks the root of the attack.
2. **Re-index the corpus by pattern rather than vertical.** Cheapest and highest
   leverage, because it is a multiplier on data already held rather than a new
   data source.
3. **Decide about distribution.** Their real weapon is that creators come for the
   builder and stay for the audience. Either pick a vertical where we can build
   that loop, or accept competing on generation quality alone - which is the axis
   that commoditises fastest.

**Two defenses that were tested and failed:** "we have more users" does not
survive, because density inside a domain beats volume across all of them. Neither
does "our personalization is better" - a well-styled app nobody uses is still an
app nobody uses.
