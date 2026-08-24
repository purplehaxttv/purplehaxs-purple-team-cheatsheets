# A closer look at Discernment

Parent: [Course overview](./README.md)
Previous: [Effective prompting techniques](./09-effective-prompting-techniques.md)
Next: [The Description-Discernment loop](./11-the-description-discernment-loop.md)

## The point

Discernment is the flip side of Description: Description communicates your intentions clearly; Discernment evaluates whether what you get back actually meets your needs. Three types, mirroring Description's own three-way split (Product/Process/Performance).

## The three types of Discernment

- **Product Discernment** — evaluating the quality of the actual output: is it factually accurate, appropriate for audience/purpose, coherent, does it meet requirements and actually add value?
- **Process Discernment** — assessing *how* the AI arrived at the output: logical errors, attention lapses, inappropriate steps, getting stuck on one detail, circular reasoning. A concrete failure mode to watch for: expanding one of several outline options, then noticing rejected ideas creeping back in after several rounds of back-and-forth — that's Process Discernment catching a real failure.
- **Performance Discernment** — evaluating how the AI *behaved* during the interaction: is there a better way for it to communicate for ease/productivity, does it respond well to feedback, is the interaction efficient (too many clarifying questions when you wanted concise answers, or too brief when you needed depth)?

**On what to do once Discernment flags a problem:** effective feedback specifies what the problem is, explains why it's a problem, gives concrete suggestions, and revises instructions/examples — "when discernment flags a problem, better description is often the solution." But not always: sometimes the fix isn't better Description at all, it's revisiting the Delegation decision itself — wrong tool, or the wrong approach to the problem entirely. Worth remembering: Discernment doesn't just feed back into Description, it can bounce all the way back to Delegation.

## Ties to the 4Ds

This *is* the Discernment lesson, and it explicitly cross-references Description (its counterpart): the two form a matched pair, each split into the same three dimensions (Product, Process, Performance) applied in opposite directions — Description sends structured input, Discernment evaluates structured output.

## How this connects to the companion course

Process Discernment — "logical errors, attention gaps, inappropriate reasoning" — is the practical checklist version of what the [AI Capabilities and Limitations](../ai-capabilities-and-limitations) course explains mechanistically: a plausible-sounding wrong answer is [Next Token Prediction](../ai-capabilities-and-limitations/04-next-token-prediction.md) doing fluent completion without grounding, and reasoning drift over a long exchange is [Working Memory](../ai-capabilities-and-limitations/06-working-memory.md) and [Steerability](../ai-capabilities-and-limitations/07-steerability.md) colliding (per that course's [When Properties Collide](../ai-capabilities-and-limitations/08-when-properties-collide.md) lesson). This lesson tells you *what to watch for*; the companion course tells you *why it happens*.

## Key takeaway to land

Discernment isn't a single "is this good?" judgment — it's three separate questions (is the output right, was the reasoning sound, was the interaction itself well-behaved), and conflating them is how a good-sounding-but-wrong output slips past review.

## Exercise: Expert Discernment — Evaluating AI Responses in Your Domain

**Why:** domain expertise is what makes Discernment possible at all — this exercise deliberately uses a topic you already know well, so you can actually catch what's wrong.

1. Pick a topic you're genuinely knowledgeable and passionate about.
2. Ask Claude for three different explanations/analyses of a specific aspect of that topic.
3. Apply all three Discernment types to each explanation: Product (accuracy, factual errors, appropriate detail level), Process (logical reasoning, gaps, appropriate connections), Performance (attentiveness to your question, terminology, tone/clarity).
4. Identify the strongest and weakest explanations with specific reasoning; work with Claude to produce an improved version.
5. Reflect: what expertise let you catch strengths/weaknesses a non-expert would miss?

A useful variant: deliberately ask for three explanations of varying quality (or plant known flaws in two of them if you're testing this on yourself) — an unsubstantiated blanket claim in one, a flatly false "always" claim in the other. It's easy to catch Product accuracy issues and an overconfident tone (Performance) on instinct; the habit that takes more deliberate practice is Process Discernment — separately naming *when an explanation skipped the actual reasoning chain and just asserted a conclusion*, even when your gut already correctly flagged that explanation as the weakest one.

## Signals worth watching for across any domain

- **Overconfidence** stated with no hedge on a claim that should carry uncertainty.
- **Fast answers on time-sensitive/evolving topics with no visible tool usage** — if a claim about something recent or fast-changing gets answered instantly with no search/tool call shown, that's a signal it's coming from static training knowledge, which may be stale.
- **Absolute language** ("always," "never," "basically any account").
- **Claims with no checkable source attached.**
- **Internal inconsistency across a longer conversation** — the working-memory/steerability failure mode the companion course names directly.
