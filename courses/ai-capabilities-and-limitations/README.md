# AI Capabilities and Limitations — Companion Notes

A lesson-by-lesson companion to Anthropic's Claude Academy course *AI Capabilities and Limitations*. Where the [AI Fluency Framework](../ai-fluency-framework-and-foundations) covers the *human* side of AI collaboration (the 4Ds), this course covers the *machine* side: what the model is actually doing when prompted, and why. Understanding one sharpens the other — you can't delegate well without knowing where a model is strong or weak, and you can't evaluate its output without a picture of how that output got produced.

Deliberately built to survive product churn: it teaches the *shape* of four core properties (next-token prediction, knowledge, working memory, steerability) rather than current numbers, since context windows and hallucination rates change every release but the underlying mechanisms don't.

## Lessons

1. [Intro to AI Capabilities and Limitations](./01-intro.md) — course roadmap, why this pairs with the 4Ds
2. [What we mean by AI](./02-what-we-mean-by-ai.md) — generative vs. everything-else AI, and the capability/limitation continuum
3. [Pretraining and Fine-tuning](./03-pretraining-and-fine-tuning.md) — the two training stages and their behavioral fingerprints
4. [Next Token Prediction](./04-next-token-prediction.md) — fluency and hallucination as the same mechanism
5. [Knowledge](./05-knowledge.md) — training-time-only knowledge, the cutoff, staleness, uneven coverage, bias, source amnesia
6. [Working Memory](./06-working-memory.md) — the context window as a hard cliff, not a gradual edge
7. [Steerability](./07-steerability.md) — instruction-following as pattern-completion, not understanding
8. [When Properties Collide](./08-when-properties-collide.md) — most real failures are two properties meeting at once
9. [Course Wrap-Up](./09-course-wrap-up.md) — the two frameworks as one system, calibrated trust as a habit

## Course arc

1. **Two training stages** — pre-training (builds a document completer) vs. fine-tuning (shapes it into an assistant) — and the fingerprint each leaves on the finished model's behavior.
2. **Four core properties**, each a continuum to calibrate a task against: next token prediction, knowledge, working memory, steerability.
3. **Interconnections** — most real-world AI failures are two properties intersecting (e.g. a hallucinated citation = next token prediction meeting a knowledge gap; long-conversation drift = working memory meeting steerability). Naming the combination tells you why it happened and what to do about it.

Exercises throughout are meant to be run against your own real tasks, documents, and niche topics — the goal is calibration you can feel, not term memorization.
