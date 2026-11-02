# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

**Product:** Sketch To Click Studio — sketch in, deployed full-stack app out.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | **3**/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | **4**/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | **2**/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | **3**/5 |

### Correction Loop - 3/5
*Revised down from 4 after the breakout. The loop is strong inside the editor and
blind outside it.*

**What you capture today:**
Everything that happens before the user leaves the editor. Each session yields a
paired before/after with human intent attached - the sketch, the first
generation, the fixes made, the version accepted - captured in our own backend
and fed into a shared asset, so a user who never corrected anything benefits from
corrections made before they arrived. Dense, free to collect, genuinely
unavailable elsewhere.

**What you miss, and it is the expensive half:**
Everything that happens after. A generated app ships, and three weeks later it
leaks on the checkout flow, or an RLS policy exposes rows it should not, or an
edge function fails under real concurrency. We never see it. The user either
fixes it somewhere else, prompts us again with no error context attached, or
leaves it broken. Either way the lesson does not reach the corpus.

The distinction matters because the two halves teach different things. In-editor
corrections teach *intent* - does this match what they drew. Post-deployment
failures teach *correctness under real conditions*, which is where the costly
mistakes live and where a domain's hard-won rules actually come from.

**How it compounds:**
It compounds on intent and not at all on outcome. That is the ceiling: a corpus
that gets steadily better at producing output people approve of, while learning
nothing about whether the approved output worked.

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

**Total Flywheel Score: 12/20**

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

*Captured from the breakout. The attack is my sparring partner's; the timeline is
structured around her two points, which are quoted as she made them.*

**Attacker:** A vertical specialist creator platform, played by my partner.

**Attack vector (target the weakest loop):**
Two loops at once, and the second makes the first worse.

> "On the corrections loop, making sure failures that happen after leaving the
> editor are captured would be a differentiator. When you're building in Lovable
> and you encounter a checkout flow leak, Lovable might never see and fix or
> learn from that error."

> "On the domain context, Lovable learns whether code looks acceptable and as a
> competitor I would learn whether it succeeds. In my vertical, Lovable's scale
> and generic corrections would lose to my proven outcomes."

**Weeks 1-4 - what they ship:**
A builder for one vertical that instruments the deployed app, not just the
editor. Every production error - a checkout leak, a failed payment webhook, a
data exposure - is captured, attributed to the generated code path that caused
it, and fed back into generation. Their corpus starts learning from outcomes on
day one.

**Weeks 5-8 - how they poach users:**
The pitch is proof, not polish: "apps built here fail less in production, and
here is the number for your vertical." Our users who have already hit a
post-launch failure we never heard about are the easiest to convert, because the
attacker can name a problem we do not know exists.

**Weeks 9-12 - why users don't come back:**
Because the gap compounds in a direction we cannot see. Their generator learns
which patterns break in production; ours learns which patterns get approved in
the editor. Those diverge exactly where the stakes are highest, and we only
discover it from churn.

**Your defense:**
She is right today, and in her vertical she wins today. The defense is that we
can close this loop faster than she can scale, for one structural reason: **we
already host the apps.** The database, auth, storage and edge functions run on
our infrastructure, and we already collect their logs, edge function success
rates and security scan results for debugging. The outcome signal she is
building is flowing through our systems right now. We simply never route it back
into generation.

1. **Join runtime failures to the generation that produced them.** Both sides -
   the generated code and the production logs - already sit in one system. Every
   error becomes an outcome label, generated automatically, without asking a user
   anything. This closes the truncated correction loop.
2. **Index those failures by pattern, not by vertical.** A checkout leak, an RLS
   misconfiguration, an auth bypass recur across every domain, so runtime
   failures are the natural seed for a pattern index. One mechanism fixes both
   weak loops: Correction stops ending at the editor, and Domain Context gets the
   pattern-shaped corpus it was missing.
3. **Concede the vertical she has already won, and race for the rest.** A
   specialist with proven outcomes in one domain will hold it. The race is
   whether we close the loop across every other domain before specialists appear
   in them. The window is roughly two quarters.

**What does not work as a defense:** "we have more users" (density inside a
domain beats volume across all of them) and "our personalization is better" (a
well-styled checkout that leaks is still a checkout that leaks).
