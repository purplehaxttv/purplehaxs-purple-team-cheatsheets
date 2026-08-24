# What we mean by AI

Parent: [Course overview](./README.md)
Previous: [Intro to AI Capabilities and Limitations](./01-intro.md)
Next: [Pretraining and Fine-tuning](./03-pretraining-and-fine-tuning.md)

## The point

"AI" is broad enough to be nearly meaningless without a split. Recommendation engines, spam filters, fraud detection, customer-service routing — all AI, none of it generative. Those systems sort, rank, classify, predict. This course is specifically about **generative** AI: systems that produce new content — text, images, code, audio, video — rather than categorizing existing content.

Two training stages build a generative model:
1. **Pre-training** — trained on massive data to learn patterns.
2. **Fine-tuning** — refined to be broadly safe, ethical, helpful.

(Detail on both stages is in the next lesson.)

**Generative AI at its core is a prediction system.**

## The capability/limitation continuum

AI isn't uniformly capable or uniformly unreliable — it's strong and weak along specific, predictable axes, and most of the time **the strength and the weakness come from the exact same underlying property.** A model writes compellingly *because* it's a prediction engine; it hallucinates for the identical reason. The mechanism never changes — what moves is where a given task happens to land on that line.

Framed as **calibrated trust** — neither blanket distrust nor full delegation. The end-state question: *"Where does my task sit on the continuum for each property? Is this well-trodden territory or am I near an edge? What are the stakes if I'm wrong?"*

## The four properties, previewed

1. **Next token prediction** — where answers actually come from. Absent an external source/tool, the model isn't looking anything up — it's writing what comes next based on training content, one fragment at a time.
2. **Knowledge** — broad but uneven, frozen at a training cutoff, shaped entirely by what was in the training data.
3. **Working memory** — what's in the context window is what's available; models don't have unlimited memory, same as humans.
4. **Steerability** — remarkably directable, but there's a gap that can open between intent and what actually lands.

## Key takeaway to land

Generative AI's failures aren't bugs bolted onto an otherwise-reliable system — they're the same mechanism that produces its strengths, just landing on the wrong end of the same continuum for a given task. Knowing the mechanism lets you predict, ahead of time, where a task is likely to land.
