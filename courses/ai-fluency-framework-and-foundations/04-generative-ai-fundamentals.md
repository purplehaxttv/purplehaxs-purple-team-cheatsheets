# Generative AI fundamentals

Parent: [Course overview](./README.md)
Previous: [The 4D Framework](./03-the-4d-framework.md)
Next: [Capabilities and limitations](./05-capabilities-and-limitations.md)

Taught by Drew Bent (Anthropic).

## The point

Generative AI is defined by *creating* new content, not just analyzing existing data — the example given: traditional AI classifies an email as spam/not-spam, generative AI writes a brand-new email.

## The three developments that made this possible (as stated)

1. **Algorithmic/architectural breakthroughs** — the transformer architecture (2017) as the gamechanger: it processes text sequences while maintaining relationships between words across long passages, critical for context.
2. **Explosion of digital data** — the training material: websites, code repositories, and other text representing human knowledge and communication.
3. **Massive compute increases** — GPUs/TPUs and distributed clusters made training at this scale possible.

Combination of the three produced **scaling laws**: performance improves predictably as models grow larger with more data and compute — and, more surprisingly, **emergent capabilities** appear that weren't explicitly programmed (step-by-step reasoning, adapting to new tasks with minimal instruction).

## How training actually works (as stated)

- **Pre-training** — the model analyzes patterns across billions of text examples, predicting what comes next, refining until it builds "a complex map of language and knowledge." Not retrieval — the model generates new text that statistically follows from the prompt, it isn't pulling pre-written answers from a database.
- **Fine-tuning** — the model learns to follow instructions, be helpful, and avoid harmful content, using human feedback and reinforcement learning (rewards/penalties shaping the model toward helpful/honest/harmless).
- **Context window** — described explicitly as "the AI's working memory": includes the prompt, responses, and everything shared in the conversation so far. The model has no access to anything beyond it without specialized tools like web search.

## Three characteristics that make generative AI powerful (as stated)

1. Learning complex, nuanced patterns from vast training data.
2. **In-context learning** — adapting to new tasks from instructions/examples in the prompt, with no additional training required.
3. **Emergent capabilities from scale** — abilities that arise unplanned as models grow, sometimes surprising even their creators.

## Ties to the 4Ds

Not explicitly connected in this lesson — it's laying technical groundwork (Deep Dive 1) rather than applying a competency. The connection is implicit: understanding pre-training/fine-tuning/context-window limits is exactly the knowledge Discernment and Delegation decisions depend on.

## How this connects to the companion course

This lesson covers, almost one-to-one, ground the [AI Capabilities and Limitations](../ai-capabilities-and-limitations) course spends multiple lessons on: pre-training vs. fine-tuning ([Pretraining and Fine-tuning](../ai-capabilities-and-limitations/03-pretraining-and-fine-tuning.md)), next-token generation ([Next Token Prediction](../ai-capabilities-and-limitations/04-next-token-prediction.md)), and the context window as working memory ([Working Memory](../ai-capabilities-and-limitations/06-working-memory.md), which specifically frames it as a "hard cliff, not a gradual edge"). The one new frame worth carrying over: this lesson names the *three enabling developments* (architecture, data, compute) as a cause explaining *why* those properties exist at all — the companion course treats them as given; this lesson explains their origin.

## Key takeaway to land

Generative AI's core trick — predicting what comes next, at scale, with a working-memory limit — is the same mechanism whether you call it "next token prediction" or "in-context learning inside a context window." Two vocabularies, one underlying model, worth being able to translate between.
