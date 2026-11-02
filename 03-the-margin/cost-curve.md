# Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | | |
| Inference (cascading/triage) | | |
| Infrastructure | | |
| Data/storage | | |
| Human-in-the-loop | | |
| **Total AI COGS** | | |

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
