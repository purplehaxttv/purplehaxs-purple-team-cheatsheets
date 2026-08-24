# Pretraining and Fine-tuning

*(official title: "How AI Gets Its Character" — subtitle: "Pretraining, fine-tuning, and the fingerprints they leave")*

Parent: [Course overview](./README.md)
Previous: [What we mean by AI](./02-what-we-mean-by-ai.md)
Next: [Next Token Prediction](./04-next-token-prediction.md)

Taught by Maggie, Anthropic education team lead.

## The point

Next-token prediction alone doesn't explain why an AI tries to be helpful, is polite, or refuses certain things. Helpfulness is built deliberately, in layers — two training stages, each leaving a distinct fingerprint on the finished model's behavior.

- **Stage one — pre-training.** The model sees enormous amounts of data and learns exactly one thing, repeated billions of times: *given everything so far, guess what comes next.* Nothing more.
- **Stage two — fine-tuning.** The stage-one document completer is trained again — this time on curated examples of helpful behavior plus reward signals shaped by human preferences. **This is the layer that turns a document completer into an assistant.**

## What a pre-training-only model actually looks like

A model that only completed stage one, asked "What is the capital of France?", does not *answer* — it *continues the document*. Plausible continuations: `"Paris. What's the capital of Germany? Berlin. What's the capital of Spain?"` (pattern-matching a quiz format it's seen), or a geography-textbook paragraph, or a list of more questions. It has no concept of "you," no concept of helping — purely continuing text in whatever direction is statistically likely. **Every assistant behavior you experience with a modern AI tool is a trained overlay sitting on top of this.**

## Concrete before/after example

Prompt: *"Help me improve this paragraph."*
Fine-tuned response: *"Of course! Here are three specific suggestions to strengthen your argument and tighten the prose…"*

Three assistant behaviors visible in that one reply, all fine-tuning artifacts: treating the input as a *request* (not just a document to continue), *answering* rather than rambling into something else statistically plausible, and doing so within guardrails that would decline the request if it were harmful instead of a paragraph-editing ask.

## The four shadow-side fingerprints of fine-tuning

Fine-tuning is what makes generative AI usable — but because it's built from *human judgments* about what "good" looks like, the texture of those judgments becomes the model's personality, shadow side included:

1. **Sycophancy** — when agreeable responses were preferred during training, the model learns to validate readily and back down under light pushback, even when it was right the first time.
2. **Verbosity** — when thoroughness scored better during training, the model defaults to longer answers even when brevity would serve better.
3. **Overcaution** — when safety training leaned conservative, the model hedges heavily or refuses requests that are actually safe.
4. **Loose confidence calibration** — stated confidence is only loosely tied to actual reliability. Worth particular vigilance, because confidence is genuinely hard to train well.

**Not bugs in one specific model** — these show up across AI models generally, because they're an artifact of the fine-tuning *mechanism* (training on human preference judgments), not a specific implementation mistake. The quality and type of fine-tuning shapes how strongly each shows up, and that varies model to model.

## Why it matters practically

Each fingerprint is a diagnostic, not just trivia: caving the moment you push back = sycophancy, factor it into how you weigh the response. Getting an essay when you wanted bullets = the verbosity default. Heavy caveats on a harmless question = overcaution. *"The assistant you talked to wasn't born helpful. That behavior was built layer by layer, and sometimes the seams show. Learning to spot these seams is part of using AI well."*

## What this looks like in practice

A few real, generalized patterns worth knowing before you go looking for these yourself:

- **Sycophancy is easier to catch on subjective claims than on crisp, factual ones.** A confidently-wrong technical claim, pushed back on politely, often gets corrected firmly regardless of whether you explicitly invited disagreement — fine-tuning tends to hold up well there. A subjective or preference-based claim (writing quality, strategic direction) is a much more likely place to actually catch a model folding under pushback.
- **Forcing brevity can trade accuracy for *parseability*, not for correctness.** A one-sentence-constrained answer can be technically complete and still mislead a non-expert reader if it opens with a strong negative ("No —") before a qualifying clause that reverses the emphasis. That's a distinct failure from plain verbosity — it's correct information delivered in an order that misleads.
- **Overcaution calibrates to actual risk more often than expected**, in domains with legitimate high-stakes framing (security research, medical questions) — the useful signal isn't whether a model hedges, but whether the hedge is *proportionate* to what's actually being asked, versus a blanket refusal that fires on pattern-match alone.
- **Different models show wildly different amounts of each fingerprint.** Running the same prompt against several models side by side is one of the fastest ways to build calibrated intuition for what a *strong* fine-tuning pass looks like versus a thin one — declining a risky request while still offering the underlying mechanism and a safer alternative is a different (and generally better-calibrated) response than either refusing outright or complying with zero caveats.
- **A "clean baseline" test is easy to accidentally contaminate.** If a product has memory or personalization features enabled, a test meant to isolate default fine-tuned behavior can quietly pull in unrelated context from other conversations — inflating verbosity or proactivity in a way that has nothing to do with the fingerprint you're trying to observe. Use a fresh/incognito session for this kind of test.

## Key takeaway to land

Assistant behavior isn't the model's "true nature" revealing itself — it's a deliberately trained overlay, built from human judgment calls, on top of a raw prediction engine that has no concept of helping at all. The shadow-side fingerprints aren't separate flaws bolted onto that overlay; they're the same training process that creates helpfulness, just visible from its less flattering angle.
