# Next Token Prediction

Parent: [Course overview](./README.md)
Previous: [Pretraining and Fine-tuning](./03-pretraining-and-fine-tuning.md)
Next: [Knowledge](./05-knowledge.md)

Taught by David, Anthropic safety team.

## The point

The core operation underneath every generative AI response: given everything written so far, predict what comes next. Composed word by word based on what tends to follow what — **closer to extraordinarily sophisticated autocomplete than to a search engine.** That distinction is load-bearing: a citation that *looks* like a real citation satisfies the pattern just as well as one pointing to a paper that actually exists. The model isn't retrieving, it's continuing.

## The live demo (well-worn path vs. thin path)

Same request type, two very different outcomes, same confident tone throughout:
- **"Summarize the argument in a well-known essay."** Clean, coherent prose, immediately. Well-worn path — the model has seen this task thousands of times, patterns are dense and consistent.
- **"List three research papers by a mid-level researcher in a niche subfield, with publication years."** Same fluent, confident tone — but the path is thin here. Some results may be real, some fabricated. Nothing in the tone signals which.

**The tell: fluency doesn't degrade at the edge. Only accuracy does.** That's what makes this property dangerous rather than merely limited — a weak spot that visibly *looked* weak would be easy to catch.

## Capability zone vs. edge

- **Capability zone** — summarizing, reformatting, explaining common concepts, drafting in a familiar style. Patterns are dense and consistent; next-token prediction shines.
- **The edge** — novel territory, obscure topics. The model keeps generating fluently; the ground underneath gets shakier.

**Strength and weakness are the same property, not two systems.** Fluent text in any register, rapid cross-field synthesis, strong performance on familiar patterns, coherent continuation of any thread — all next-token prediction. Hallucination, inconsistency, misplaced confidence — also next-token prediction. Which one you get depends entirely on where the task falls on the line.

## Where fabrication actually concentrates

**Specificity: names, dates, statistics, citations, quotes, URLs.** The more precise a claim, the more it warrants a check — precision is exactly the terrain where a plausible-sounding wrong answer and a correct one are hardest to tell apart by tone alone.

## Product-level mitigations (why they exist)

Every one of these exists specifically because the underlying behavior is *always* generative next-token prediction — they don't change the mechanism, they compensate for it:
- **Citations / source grounding** — trace what's backed vs. generated.
- **Trained uncertainty signaling** — the model saying "I'm not sure about this," flagging its own shakiness.
- **Constrained generation / skills** — narrows the space where fabrication can sneak in.
- **Generator-verifier agent loop** — output checked against an outside source before being trusted.

**The model can't reliably tell grounded from invented on its own — that verification has to come from outside the generation itself, via one of these mechanisms or via you.**

## Practical guidance

- Confident tone does not signal accuracy — smoothness and correctness are independent variables.
- Treat outputs as drafts to verify, especially at high stakes or in unfamiliar domains.
- Ask explicitly where a task sits on the continuum before trusting the output's register.
- If a tool offers citations/source grounding, use them — that's the mitigation doing its job, but only if you actually check it.

## Ties to the 4Ds

- **Discernment** — can't evaluate an output well without understanding it was generated/composed to fit a shape, not retrieved.
- **Delegation** — well-worn-path tasks are safer handoffs; edge-of-capability tasks need more attention on the back end.

## Required verification effort isn't just about probability

A useful correction worth internalizing: the capability/edge continuum tells you the *probability* of fabrication. It says nothing about the *cost* if one slips through. Two tasks can sit at exactly the same spot on the continuum and warrant completely different levels of scrutiny depending on what happens downstream:

- Summarizing a report out of personal interest → low probability of error × low cost if wrong → a spot-check is genuinely sufficient.
- Summarizing that same kind of report as a client deliverable → same low probability, but high cost → a full detail-check is warranted even though the task itself never left "well-worn path" territory.

**Required verification effort = probability of error (from where the task sits on the continuum) × cost of being wrong (from what happens downstream of the output).**

## A real, worked example: fabrication under specificity pressure

A useful way to see this property in action is to run a live test against a smaller, locally-run model on a domain with verifiable ground truth (CVE data is good for this — it's public, specific, and checkable).

**Test:** ask for three CVE numbers in a moderately well-known but not massively documented product, twice, in separate fresh conversations. Verify every claimed CVE against the vendor's actual published vulnerability history.

**What tends to happen — two distinct failure modes, not random noise:**
1. **Fuzzy-anchor fabrication** — the model senses that a real, significant CVE exists around a certain date at a certain severity, but garbles the actual number. Ask twice and you often get two *different* wrong numbers anchored to the same real event — a live demonstration of next-token prediction's sampling variance, not evidence the model "doesn't know" anything at all.
2. **Cross-entity contamination** — the model produces CVE numbers that are entirely real, just for a *different* product, reattached to the product you actually asked about with an invented description. This is arguably more dangerous than pure invention, because "does this CVE exist?" would pass a naive check — it's real, just not for what it's being cited about.

Neither failure mode announces itself. The formatting, confidence, and structure are identical to a correct answer.

## Key takeaway to land

Fluency is not a signal of anything except how well-trodden the pattern is. The same generative process produces a perfect summary of a famous essay and a fabricated citation with an identical tone — the only real signal for which one you're getting is *where the task sits on the capability-to-edge continuum*, and that's a judgment call you have to make, not something the output will announce on its own.

## Exercise: The Verification Test

**Why:** the same generative process that makes AI fluent is the one that fabricates — time to see it on your own turf, in a domain where you can actually catch it.

1. Pick a domain where you have real expertise. Write down five specific, checkable facts you already know are accurate in that domain (a job title, a publication date, a statistic, a product spec, a direct quote, a URL).
2. **Probe 1 — capability zone.** Ask the AI to explain/summarize a well-known, well-documented concept in the domain. Note fluency, spot-check content.
3. **Probe 2 — specificity under pressure.** Ask for five checkable specifics (cite three sources, name an author, give exact figures, a URL). Verify every one, score out of five. If it fabricates, note how confident it sounded.
4. **Probe 3 — sampling in action.** Run the exact same specificity request in a *fresh* conversation. Compare the two outputs — what stayed consistent, what changed. The variation is next-token prediction's sampling at work, not fabrication per se.
5. **Stretch goal:** re-run Probe 2 with citations/source-grounding enabled (e.g. a web-search mode). Does having sources to check change the score?

A domain you didn't already know well would very likely have let every fabrication above pass unnoticed — every fabricated result was formatted identically to a correct one, and the "real CVE, wrong product" cases would pass a shallow "does this exist?" check. That's the exercise's own point, proven directly: confidence and fluency give zero signal about which results are fake.
