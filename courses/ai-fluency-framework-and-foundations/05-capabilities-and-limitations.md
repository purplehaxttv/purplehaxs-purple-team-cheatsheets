# Capabilities and limitations

Parent: [Course overview](./README.md)
Previous: [Generative AI fundamentals](./04-generative-ai-fundamentals.md)
Next: [A closer look at Delegation](./06-a-closer-look-at-delegation.md)

Framed throughout as "getting to know a new colleague" — understanding strengths and limitations to collaborate more effectively, not a spec sheet.

## The point

What generative AI (LLMs like Claude) can and cannot do *right now* — with an explicit acknowledgment that the field moves fast and today's limitations aren't permanent. The takeaway isn't a fixed list, it's the habit of checking.

## What these systems do well (as stated)

- Versatile across language tasks — emails in your voice, condensing long reports, translation, explaining across wildly different fields — the same system without retraining between tasks.
- Maintains conversational thread — refers back to something mentioned earlier in the same conversation, much like a human conversation partner.
- Can reach beyond its own knowledge via external tools (web search, files, other applications) — "dramatically expands what they can help with."

## Current limitations (as stated)

- **Knowledge cutoff** — no innate knowledge past training data's cutoff date. Analogy given: someone at an internet-free retreat past a certain date — needs tools like web search to learn about anything after.
- **Hallucination** — training doesn't verify every fact, and models can misassemble learned information; "AI confidently stating something that sounds plausible but is actually incorrect." Contrasted explicitly with search engines, which retrieve real documents rather than generate statistically.
- **Context window** — a hard cap on how much can be considered at once; once exceeded, information outside the window is lost, generally first-in-first-out.
- **Non-determinism** — same question, same input, can yield different answers each time, because the model makes probabilistic next-token decisions. Good for brainstorming variety, a liability when consistency/accuracy is critical. Controllable via a "temperature" setting on some interfaces.
- **Complex reasoning** — historically weak on multi-step math/logic, though newer "reasoning"/extended-thinking models are improving here.
- **Tool/data access gaps** — even with tool use, a model without access to a specific data source or specialized tool simply can't help with tasks that need it. Analogy: a brilliant colleague locked out of your company's internal database.

## Ties to the 4Ds

Not explicitly tied to a specific D in this lesson — it's the shared factual foundation Discernment (evaluating outputs against these known failure modes) and Delegation (Platform Awareness, from [A closer look at Delegation](./06-a-closer-look-at-delegation.md), next) both depend on.

## How this connects to the companion course

This lesson restates, almost claim-for-claim, the [AI Capabilities and Limitations](../ai-capabilities-and-limitations) course's core material: knowledge cutoff ↔ that course's [Knowledge](../ai-capabilities-and-limitations/05-knowledge.md) lesson, hallucination-from-fluency ↔ [Next Token Prediction](../ai-capabilities-and-limitations/04-next-token-prediction.md), context window as a hard limit ↔ [Working Memory](../ai-capabilities-and-limitations/06-working-memory.md)'s "hard cliff, not gradual edge" framing (this lesson's own "first-in-first-out" phrasing matches that same claim). One item genuinely distinct here: **non-determinism/temperature** is named explicitly as a user-facing lever, where the companion course folds unpredictable output into the next-token-prediction discussion without naming "temperature" specifically. The reasoning-model caveat ("newer reasoning models show strong progress") also matches how the companion course's [When Properties Collide](../ai-capabilities-and-limitations/08-when-properties-collide.md) resolves a live math failure — by routing to a different capability (code execution) rather than trusting default step-by-step generation.

## Key takeaway to land

None of these limitations are secrets or edge cases — they're named plainly, with the explicit framing that the most effective use of AI comes from combining its strengths (speed, scale, pattern recognition, tireless breadth) with distinctly human strengths (critical thinking, judgment, creativity, ethical oversight) rather than expecting either to cover for the other.
