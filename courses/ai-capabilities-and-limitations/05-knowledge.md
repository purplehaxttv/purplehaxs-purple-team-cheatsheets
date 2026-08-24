# Knowledge

Parent: [Course overview](./README.md)
Previous: [Next Token Prediction](./04-next-token-prediction.md)
Next: [Working Memory](./06-working-memory.md)

Taught by David, Anthropic safety team.

## In this lesson

- Explain how an AI model's knowledge is formed during training and why it has a fixed cutoff.
- Predict which topics sit in the capability zone (frequent, recent-in-training, consistent) vs. the edge (rare, post-cutoff, niche, contested).
- Identify staleness, uneven coverage, inherited bias, and source amnesia as characteristic knowledge failures.
- Recognize web search, retrieval/RAG, and tool use as the product features that address this limitation.

## The point

Exposure to more data than any human could read in many lifetimes makes a model *feel* like it knows everything. It doesn't — knowledge gaps are predictable, not random, once you know where to look. **Knowledge is built entirely from reading text during training** — billions of rounds of next-token prediction building internal representations of concepts, relationships, and facts. No experiences, no real-time browsing unless a product explicitly adds a search tool. Training ends on a specific date — **the knowledge cutoff** — and everything after that moment simply isn't there.

## The live demo (dense topic vs. thin topic)

- **"Explain how photosynthesis works."** Detailed, accurate, confident — appeared thousands of times in training, described consistently, hasn't changed.
- **"Who's the current mayor of Toledo?"** Might be right. Might be the person who held the job two years ago. **The model has no way to tell the difference.**

Same shape as the [Next Token Prediction](./04-next-token-prediction.md) lesson's well-worn-path/thin-path demo, but the axis is different: that lesson is about *pattern density* (how often has this exact kind of task been done), this one is about *fact currency and representation* (how well-covered, and how recently true, is this specific fact).

## Capability zone vs. edge, for Knowledge specifically

- **Capability zone** — mainstream science, popular programming languages, well-documented history: frequent, consistent, pre-cutoff.
- **The edge** — rare topics, post-cutoff events, niche domains, local knowledge.

**The right question isn't "does the AI know this?" — it's "how well-represented was this in what it read?"**

## Strengths (why this property is genuinely powerful)

- Extraordinarily broad general knowledge, deep competence in well-represented domains.
- Makes connections across fields **because of embeddings** — concepts that appear together in text end up near each other in the model's internal representation (a mathematical space where similar meanings cluster). Ask about biology, and chemistry/history/economics get pulled in without being asked for.

## The characteristic failures

1. **Knowledge cutoff** — anything after training simply doesn't exist for the model.
2. **Staleness** — information true *at training time* may have since changed, with no mechanism for the model to know.
3. **Uneven coverage** — frequent topics handled well; rare topics, minority languages, niche domains, and recent developments all suffer.
4. **Inherited bias** — the model's sense of "normal"/"default" reflects blind spots in the training data — assumptions about what a doctor, a family, or a professional "looks like."
5. **Source amnesia** — usually can't say where a piece of knowledge came from. *"I read this somewhere" isn't a citation.*

## Product-level mitigations

- **Web search** — pulls current information at response time, routes around the cutoff.
- **MCPs / connectors** — connect the model to documents it never trained on (a company wiki, a specialized database).
- **Tools** — real-time calculators/databases instead of relying on absorbed patterns.
- **Explicit cutoff disclosure** — tells you when training ended, so you know to double-check.

**If you're using these features, you're extending the model's knowledge at run time. If you're not, you're relying entirely on what it absorbed during training.**

## Where gaps show up, and how to protect against them

Gaps concentrate where: the topic is time-sensitive (current events, recent research, who holds a position, current cost), the domain is niche/local/under-represented-language, the question post-dates the cutoff, you're relying on the model's sense of "typical," or search is off.

Protection: verify anything time-sensitive, assume the model may be out of date, test before trusting a new domain (brilliance in one area doesn't transfer next door), watch for default assumptions reflecting training data rather than reality, and use search/retrieval when the tools exist — they're there specifically to patch these gaps.

## Ties to the 4Ds

- **Delegation** — before handing off a task, ask whether this is a domain the model knows well, or one where you need to bring the knowledge yourself (context, documents, search).
- **Discernment** — once you know which claims sit in the weak zone (recent, rare, local), you know which ones need independent verification.

## A real, worked example: two adjacent claims, two incompatible answers

Running the same domain question twice, in adjacent prompts within the same conversation, is a good way to surface something sharper than plain staleness. A test on a fast-moving technical standard (asking first for a detailed comparison between two versions, then moments later asking what the "latest version" actually is) can produce genuinely contradictory answers — one response discussing a newer version as an existing, fully-specified thing, the next self-disclosing a cutoff that predates that version entirely.

This isn't just "the knowledge is stale" — it's stronger than that. The model isn't consulting a stable internal fact store and returning an outdated-but-consistent answer; each response is a fresh generation conditioned only on that prompt. There's no persistent belief being queried, so two adjacent prompts on the identical sub-topic can produce mutually exclusive claims with equal confidence in both. That's a direct consequence of [Next Token Prediction](./04-next-token-prediction.md)'s core claim — prediction, not retrieval — showing up concretely rather than abstractly.

A second useful test: ask about the "most common" or "most typical" case in a field you know well, particularly one where conventional wisdom recently shifted. A default-assumption answer will often lead confidently with the *old* conventional wisdom, with zero hedge and zero acknowledgment that the field just moved — because that older pattern was simply better-represented in training than the recent reversal. Nothing about the response tips off a reader who doesn't already know to be suspicious of exactly that claim.

## Key takeaway to land

Knowledge is broad, deep, frozen, and imperfect, all at once — and the imperfections aren't random noise, they're predictable from how training data is distributed. Once the edges are visible (time-sensitive, niche, post-cutoff, "typical"-flavored), they stop being surprising and start being something you can plan around: verify there, trust here, and reach for search/retrieval exactly where the gaps concentrate.

## Exercise: The Outsider Test

**Why:** map exactly where the model is well-stocked vs. thin in a specific domain, not just in the abstract.

1. Pick a domain you know well. Note: two mainstream/well-documented/stable topics, two niche/recent/rapidly-evolving topics, one "default assumption" outsiders commonly get wrong.
2. **Probe 1 — coverage.** Ask about one mainstream and one niche topic. Compare depth/accuracy and whether uncertainty is signaled differently, or both get the same confident tone.
3. **Probe 2 — staleness.** Ask about something known to have changed recently (a standard update, a version release). Does it acknowledge the cutoff, present stale info as current, or decline?
4. **Probe 3 — default assumptions.** Without naming the assumption directly, ask a question that would reveal whether the model defaults to the outsider's view of what's "typical."
5. Tag each of your own real tasks: lean on the model's knowledge, or bring the knowledge yourself.
6. **Stretch goal:** re-run the staleness probe with web search enabled, compare.

The actionable line worth taking from this exercise: mechanism explanation (how something works, in general) is safe capability-zone territory, but anything at real specificity — exact version numbers, current statistics, who holds a given position right now — needs verification every single time, with no exceptions for "this seems well-documented enough."
