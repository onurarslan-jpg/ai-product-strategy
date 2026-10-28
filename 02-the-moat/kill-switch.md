# Kill Switch Audit

**Stack under audit:** the generation path — the agent that turns a sketch into a
working full-stack app — plus the preference and correction machinery around it.

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Single frontier model family for code generation, chosen on output quality. No second source provisioned. | **H** | Provision keys and a signed fallback with a second provider so the decision on the day is "accept a known quality delta", not "start evaluating". |
| **Abstraction** | Calls go through provider-specific features — tool-call format, structured output, prompt caching. The deeper coupling is the prompts themselves, tuned over months to one model's behaviour. | **H** | Inventory every place a provider-specific feature is used. Cannot be fixed in 48 hours; knowing the size of the problem can be. |
| **Routing** | One model, one path. No split, no shadow traffic, no gradual cutover. | **M** | Move the model identifier out of code and behind a config flag, so a swap is a deploy rather than a release. |
| **Eval** | A large corrections corpus exists but no frozen, versioned evaluation set is cut from it. Quality is judged per session, not per model version. | **H** | Freeze 200 sketch → accepted-app pairs as a golden set. This is a query against data already held, not a project. |

## Portability Score
<!-- Ready / Partial / Locked -->
**Partial**, and closer to Locked than the word suggests.

Not Locked, because the hard part is already done: a corrections corpus means the
golden set is a query away, and most teams at this stage have nothing to build an
eval from at all.

Not Ready, because of a dependency the table understates. Of the four rows, Eval
gates the other three. Perfect abstraction and clean routing still leave you
unable to swap, because without a frozen eval you cannot tell whether the
replacement is worse — and "it feels worse" does not survive contact with a
pricing deadline. Prompt coupling is the second trap: it is invisible in an
architecture diagram, it never appears in a dependency audit, and it is the thing
that actually takes a quarter to unwind.

## If [primary vendor] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->
The honest answer is that you do not swap in 48 hours, and planning as though you
might is how teams end up shipping a quality regression they cannot measure. In
48 hours you buy time on the demand side, then run the swap on eval time.

1. **Cap retries per generation immediately.** Retries are a large and invisible
   share of per-app cost, and capping them is a config change with a measurable
   ceiling. This is the single biggest same-day lever.
2. **Split the workload by value, not by volume.** First generation keeps the
   frontier model, because that is where acceptance is won. Small edits,
   preference application and re-renders move to a cheaper model, where the
   quality delta is tolerable and the volume is highest.
3. **Start the eval-gated swap on day one, and tell finance it lands in weeks.**
   With a golden set frozen, a real swap decision takes days of evaluation. With
   no golden set, it takes a quarter and arrives as a guess.

## If [primary vendor] ships a competing product:
<!-- What's defensible that they can't replicate? -->
Not the generation step. They own the model, so they will match or beat the raw
output, and competing on that axis is a losing fight.

What they cannot see is the *outcome* layer. Through an API they observe prompts
and completions. They do not observe which of five generations a user finally
accepted, what the user changed before accepting it, or the accumulated team
profile built from a year of those decisions. Corrections and preferences are
labels applied after the model has finished — they exist in our backend and
nowhere else.

Two caveats that turn this from a comfort into a task. First, it only holds under
no-training and zero-retention terms; on standard API terms the raw text is not
as private as this argument assumes, so get that in the contract. Second, the
asset is only defensible to the extent the label is good — acceptance is a proxy,
and a provider with outcome telemetry of their own would have better labels than
ours. That is the same gap M2 names as the primary threat, arriving from a
different direction.

---

## Three Actions to 48-Hour Swap Readiness

**This week — cut the golden set.**
Freeze 200 sketch → accepted-app pairs from the corrections corpus, plus 20
adversarial cases that are known to be hard. Version it. In the same change, move
the model identifier behind a config flag. Both are days of work and together
they convert a swap from a gamble into a measurement.

**This month — make the fallback real.**
Route one low-risk, high-volume path to a second provider behind that flag and
score it against the golden set. The output is a number: what a swap costs in
quality, per path. A fallback that has never served traffic is not a fallback.

**This quarter — unwind the prompt coupling.**
Move provider-specific features behind an internal interface and maintain the
system prompts model-agnostically, with per-model adapters rather than one tuned
artifact. Finish by getting no-training and zero-retention terms signed, since
the entire defensibility argument above depends on them.
