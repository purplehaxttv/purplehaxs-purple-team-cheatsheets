# Course Wrap-Up

*(closing lesson page title: "A Small Model of the Machine" — recap framework: "AI Capabilities and Limitations Framework")*

Parent: [Course overview](./README.md)
Previous: [When Properties Collide](./08-when-properties-collide.md)

Taught by Kristen, Anthropic education team (same instructor as the course intro).

## The point

The course opened with some version of "why does AI do that?" It closes with something more durable than a list of answers: **a structure that answers the next "why does it do that?" without needing a new lesson.** Models change, edge cases surprise people, the properties remain. What's been built across this course is the ability to stop being surprised.

## Recap — two training stages, four continuums, intersections

- **Two training stages** ([Pretraining and Fine-tuning](./03-pretraining-and-fine-tuning.md)): pre-training builds a document completer, fine-tuning layers an assistant on top. **Every behavior traces back to one of these two fingerprints.**
- **Four properties, each a continuum** ([Next Token Prediction](./04-next-token-prediction.md), [Knowledge](./05-knowledge.md), [Working Memory](./06-working-memory.md), [Steerability](./07-steerability.md)): capability zone, limitation zone, and product features that push the edge further out. The same mechanism is always running — what changes is where a given task lands on the line.
- **Intersections** ([When Properties Collide](./08-when-properties-collide.md)): most failures are two properties meeting at once. Diagnosis is "which two collided," not "what broke."

## The framework recap page

| Property | The question it answers | Capability zone | Limitation zone |
|---|---|---|---|
| Next Token Prediction | Where do AI answers come from? | Well-worn paths: summarize, reformat, explain common concepts | Novel territory, sparse patterns, "true vs. sounds true" |
| Knowledge | What does AI actually know? | Frequent, recent-in-training, consistent: mainstream topics, popular languages | Rare, post-cutoff, niche, local, or contested topics |
| Working Memory | What is the AI paying attention to right now? | Material fits comfortably, session is current, relevant context supplied | Very long docs/conversations, expecting cross-session continuity (the cliff) |
| Steerability | How much am I in control? | Short, concrete, verifiable instructions ("respond as a table," "under 100 words") | Long reasoning chains, abstract asks, native precision |

## Where the two frameworks meet

The 4Ds (Delegation, Description, Discernment, Diligence, from the [AI Fluency Framework](../ai-fluency-framework-and-foundations)) are *what you do*. The four properties are *what you're responding to* when you do it — not two systems to juggle, opposite sides of one coin.

- **Next Token Prediction → sharpens Discernment.** Fluency and accuracy are independent variables; knowing that changes how you evaluate output.
- **Working Memory → sharpens Description.** Context is leverage; you stop assuming the model remembers what it was never shown.
- **Steerability → sharpens Delegation.** You know where control is tight and where it thins out, so you know what to hand off versus checkpoint.
- **Knowledge ties to both Delegation and Discernment** — bring the knowledge yourself vs. trust the model, and verify claims that sit in the weak zone.

## Calibrated trust is a habit, not an attitude

The internal check, run before handing something off: *Is this well-worn territory or sparse? Recent or stable? Comfortably inside the context window? Are my instructions concrete, or is there room between my words and my intent?* Then adjust — more verification where fabrication concentrates, more context where the model can't guess intent, more checkpoints when a reasoning chain runs long. **"You don't trust the AI, but you don't distrust it either. You locate the task and set your habits accordingly."** That line is given as the definition of AI Fluency itself, not just a tip.

## Where to go from here

Practice against real work — the mental model of AI sharpens by testing predictions against actual output, not by memorizing more terms. If you haven't already, pair this with the [AI Fluency Framework](../ai-fluency-framework-and-foundations) course, which covers the human-competency side (the 4Ds) that this course's model-behavior side is meant to pair with. Keep pushing on the edges deliberately, since edges move as models improve — the specific numbers (context window size, hallucination rate) will keep changing, but the *shape* of these four properties won't.

## A note on how this holds up across model tiers

Every property in this course can be demonstrated with a small, locally-run model, not just a frontier one — and the *shapes* of the failures (hallucination on niche specifics, cliff-like memory loss, letter-over-spirit, reasoning drift, uncaught arithmetic) show up regardless of model tier. The specific boundary (how niche a topic has to be before it fabricates, how long a chain has to run before it drifts) differs model to model; the four-property structure itself doesn't need adjusting to explain what you're seeing, whichever model you're using.

## Key takeaway to land

"What went wrong" almost always decomposes into a specific two-training-stage origin and a specific two-property collision, nameable before you even see the next failure. The clearest evidence for this across the whole course isn't abstract — it's the live incidents: fabricated citations, failed builds, and confidently-wrong arithmetic all resolved into the same small vocabulary once diagnosed, and naming the pair correctly consistently produced a fix that worked where the naive fix ("try again") had already failed.
