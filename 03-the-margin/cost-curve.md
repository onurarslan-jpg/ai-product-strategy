# Cost Curve & Pricing Strategy

## Cost Model

*Modelled, not measured. Per typical active paid user per month, built from the
assumptions below. Replace any assumption with a real figure and the row it
feeds should be recalculated.*

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $7.95 | 6 first-generation runs at ~$0.65 plus 36 escalated edits at ~$0.11. $1.30 of this is retries - the cheapest line to cut. |
| Inference (cascading/triage) | $3.26 | 84 edits on the cheap model at ~$0.04 plus a routing check on every message. Saves ~$6.30 against sending the same edits to the frontier model. |
| Infrastructure | $4.00 | ~3 live deployed apps at ~$1 each (hosting, database, functions, auth) plus ~$1 of build and preview sandboxes. Scales with live apps, not with usage. |
| Data/storage | $0.60 | Corrections corpus, preference profiles, app file storage. About $0.30 is runtime logs for the M2 outcome loop. |
| Human-in-the-loop | $0.50 | Support escalations, security-review spot checks, golden-set labelling. No human sits in the generation path. |
| **Total AI COGS** | **$16.31** | About $4.08 per app built. |

**Assumptions:**
- Usage: 4 new apps a month at 1.5 first-generation attempts each, and 120 edit
  messages, of which the cascade keeps 70% on the cheap model.
- Prices per million tokens: frontier $3 input / $15 output, cheap $1 / $5,
  cached input billed at 10% of list. Placeholder list prices, not a quote.
- Token shape: a first-generation run is ~200k input (60% cached) and ~25k
  output; an edit is ~80k input (80% cached) and ~3k output.
- Infrastructure is a per-app platform cost, not a public cloud list price.

**What it says, if the assumptions hold:**
- **Margin is thin.** Against the 20 EUR/month price point in kill criterion 4,
  $16.31 of AI COGS leaves roughly 18% before anything else is paid for -
  treating EUR and USD as comparable at this level of precision.
- **Kill criterion 4's cost leg trips.** About $4.08 per app is double the 2 EUR
  threshold. The bet survives only if willingness to pay sits well above 20 EUR.
- **Caching is load-bearing.** Without it, inference alone rises from $11.21 to
  about $24.21 - more than the price of the plan.
- **Levers in order of size:** caching hit rate, then cascade ratio, then the
  retry cap.

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:**
**Frontier model:**
**Routing rule:**
**Expected cascade ratio:**

## Pricing Model

**Current pricing:**
**Proposed AI pricing:**
**Model:** seat-based / usage-based / outcome-based / hybrid

### Packaging: Leaders, Fillers, Killers
*Ramanujam's split from Monetizing Innovation. Classified from the product's
feature set, not from willingness-to-pay data - upgrade behaviour should overrule
any of these calls.*

**Leader - prompt or sketch to a working, deployed full-stack app.**
Database, auth, storage and a live URL in minutes, with no setup. It is in every
tier because without it there is no product. The stronger form of the Leader is
"it works on the first try": buyers pay for the generation landing, not for the
act of generating.

**Fillers - round out a tier, never charged for on their own.**
- Design templates, design systems, custom fonts, component libraries
- Version history, drafts, remix
- Desktop, mobile, Slack, Telegram and ChatGPT entry points
- Browser testing and security scans

Personalization belongs here at the point of purchase - nobody signs up for "it
learns our house style" - but it behaves like a Leader for retention. It goes in
every tier and stays off the pricing page as a reason to buy.

**Killers - carve out of the base offer.**
- **Enterprise governance** (SAML SSO, audit, managed registries, compliance
  controls). Worth a great deal to a small segment and nothing to the rest;
  bundled into a base tier it raises the price for everyone. Enterprise tier.
- **Expensive AI features inside generated apps** (video, music, live voice).
  Niche demand, high inference cost. Bundled, they force every plan to be priced
  for the heaviest users. Usage-based add-ons.
- **Data-warehouse connectors** (Databricks, BigQuery, Redshift). Same pattern:
  high value for a few, dead weight for most. Enterprise tier or add-on.
- **The platform badge on a paid app.** A killer that repels rather than costs.
  On a free tier it is a useful fence; on a paid plan, anyone deploying for real
  customers wants it gone, and keeping it would cut what they will pay.

**Future Leader candidate - apps that break less in production.** If the M2
defense lands and runtime failures feed back into generation, "fails less after
launch" becomes something a buyer pays for directly. It is also the exact claim a
domain specialist competes on, so it moves from infrastructure to the pricing
page the moment it is measurable.

**How it maps to the cost model:** Leaders set the base price, Fillers sweeten
the tiers, Killers become add-ons or a separate tier. The Killers line up almost
exactly with the heaviest cost lines, which is why they are Killers - bundled in,
they make every customer pay for what a few consume.

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | | |
| Heaviest segment doubles | | |
| Model provider raises prices 50% | | |

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):**
**After (AI-enabled):**
**Net margin shift:**
