# AI Product Strategy - working context

A six-module course repo (Product School). Each class adds one module; each lab
slide maps to one file. Onur shares the slide, Claude drafts the file, Onur
corrects, then it is committed and pushed.

## The product

**Sketch To Click Studio** - sketch or whiteboard photo in, deployed full-stack
app out (UI, Postgres, auth, storage, hosting). Built with Lovable; published at
https://sketch-to-click-studio.lovable.app/ (as of 28 Oct 2026 the URL served
Lovable's starter page, not the app - unresolved).

**Competitive framing (Onur's call, 2 Nov 2026):** we hold the *generalist
creator platform* position - "we are the Lovable". Lovable is a peer, not a
landlord. The threat is a **domain specialist** creator platform (worked example:
Astrocade, AI casual mobile games - genre-indexed, graded on plays, runs an
academy). Platform exposure points at the model layer (OpenAI / Anthropic).

## Current scores

| Module | Item | Score |
|---|---|---|
| M1 diagnostic | Moat / Data / Platform | 3 / 3 / 2, confidence M |
| M2 flywheel | Correction / Preference / Domain / Network | 3 / 4 / 2 / 3 = 12/20 |
| M2 kill switch | Provider / Abstraction / Routing / Eval | H / H / M / H, Partial |

Facts Onur confirmed, not inferred: users correct outputs and corrections are
captured and benefit *all* users; preferences are captured and applied
automatically.

Two findings drive everything since: (1) corrections are filed by industry, not
UI pattern, so nothing transfers between domains; (2) the correction loop ends at
the editor - production failures (e.g. a checkout leak) never reach the corpus.
Defense: we host the apps and already log runtime failures, so join those logs
back to generation and index them by pattern.

## Inputs already committed that M3 (The Margin) needs

`03-the-margin/cost-curve.md` wants a per-user cost model, a cascading strategy,
pricing model, three stress tests and a board one-pager. Already decided upstream:
- Kill criterion 4 (`01-the-bet/prototype.md`): kill if median cost per accepted
  app (generation + retries + hosting/backend) exceeds 2 EUR while under 20% of
  PMs would pay 20 EUR/month. These numbers are Claude's placeholders, not Onur's.
- Cascade (`02-the-moat/kill-switch.md`): frontier model for first generation,
  where acceptance is won; cheaper model for edits, re-renders and preference
  application, where volume is highest. Cap retries per generation - large,
  invisible share of cost, pure config.
- The runtime-failure loop adds log storage and processing cost; price it in.

Still needed from Onur before M3 can be more than a draft: real or target
pricing, token cost per generation, generations and retries per user per month,
hosting cost per deployed app, and the share of users on paid plans.

## Conventions

- **Scoring direction:** 5 = strongest position on every axis, so a low Platform
  Exposure score means *more* exposed. State this in any scored file.
- **Never invent Onur's strategy silently.** Where a field is inferred, say so in
  chat and keep the file clean. Quote the sparring partner verbatim and mark any
  structuring as Claude's.
- **Commits** go out as `Onur Arslan <265886449+onurarslan-jpg@users.noreply.github.com>`
  (global git config). Never use the work email - it was scrubbed from history.
- Push over HTTPS uses the "Claude Code course" fine-grained token in the macOS
  keychain; it expires 7 Dec 2026. A 403 on push means token scope or expiry.
- Anything Onur will send as himself (Slack, DMs): use the `my-writing-style`
  skill. exmox is always lowercase.
- The README summary blocks are intentionally left unfilled - Onur said no need.
