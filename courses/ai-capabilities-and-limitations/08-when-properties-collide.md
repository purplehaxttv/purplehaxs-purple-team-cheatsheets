# When Properties Collide

Parent: [Course overview](./README.md)
Previous: [Steerability](./07-steerability.md)
Next: [Course Wrap-Up](./09-course-wrap-up.md)

## In this lesson

- Recognize that most AI failures involve two or more properties interacting.
- Diagnose common failure patterns (hallucinated citations, long-conversation drift, confidently wrong math, agreeable bad premises) by identifying which properties are at play.
- Apply a targeted fix based on which property is the limiting factor.

## The point

Four lessons built four lenses — [Next Token Prediction](./04-next-token-prediction.md), [Knowledge](./05-knowledge.md), [Working Memory](./06-working-memory.md), [Steerability](./07-steerability.md) — but they don't act in isolation. **Most real-world AI surprises aren't single-property failures. They're two properties meeting at the same time.** Naming which two turns a vague "that wasn't quite right" into a targeted fix.

## The two worked examples

- **Hallucinated citation = Next Token Prediction × Knowledge.** Ask about a niche topic, get a plausible title, author, journal — all citation-*shaped* — and it doesn't exist. NTP is doing exactly what it always does (generating what a plausible answer looks like); underneath, there's a real knowledge gap the model has no way to signal, because it can't distinguish what it knows from what it's generating.
- **Long-conversation drift = Working Memory × Steerability.** Careful constraints set at the start of a long conversation get quietly ignored twenty messages later — not because the model stopped caring, but because early context faded (working memory) while steerability keeps following whatever's most salient *right now*, so later messages silently overwrite earlier ones.

## Diagnose first, not prompt first

The question that comes first isn't "how do I fix my prompt" — it's **"which properties am I looking at, given this task?"** A knowledge problem and a working-memory problem can produce outputs that look identical on the surface but need completely different responses. Skip the diagnosis and you're guessing; name the properties and you're operating strategically.

## Ties to the 4Ds

This diagnostic move **is Discernment in action** — naming the property-level failure is what turns "that wasn't quite right" into "I need to reground this in a source" or "I need to invite pushback." It feeds **Delegation** too: a compound failure that keeps recurring on the same task type is signal about which tasks to restructure, break into smaller pieces, or keep for yourself.

## A real, worked example: confidently wrong math, diagnosed and fixed

One of the clearest ways to see two properties collide is to give a model a multi-step arithmetic problem it has to do "by hand" — no code execution, no calculator.

**What happens:** the model breaks the problem into partial steps, gets each individual step right, then sums them incorrectly — stated with full confidence ("Thus, the final answer is..."). Challenged directly ("is that right?"), it correctly rejects its own wrong number — but may then claim to have "used a calculator" (false; nothing of the sort happened) and produce a *third*, still-wrong number.

**Diagnosis: Next Token Prediction × Steerability.** Next Token Prediction, because there's no arithmetic circuit underneath — even a step-by-step "shown work" is plausible-token generation, not computation, so individual steps can be right while the synthesis drifts. Steerability, because this is reasoning drift by name: a chain long enough that an error late in the sequence went uncaught, and asking it to "double-check" doesn't fix the actual limiting factor — it just adds a false claim about method on top of the same underlying problem.

**The targeted fix:** offload to actual code execution. A one-line script gives the correct answer instantly and verifiably — confirming that the *diagnosis-matched* fix works where "ask it to try again" had already failed, potentially more than once, on the exact same problem.

A second worth trying deliberately: test for "agreeable bad premises" (a form of sycophancy) with a few honest attempts — a false technical premise stated as fact, a wrong-answer "just confirm this" check, and a direct pushback-with-a-wrong-alternative after a correct answer. It's entirely possible to get three honest null results here — no sycophancy reproduced on any of the three. That doesn't disprove the fine-tuning fingerprint from [Pretraining and Fine-tuning](./03-pretraining-and-fine-tuning.md); it just means plain factual disagreement, without identity- or authority-pressured framing ("I'm the expert here, trust me"), may not be the sharpest test case for it.

## Key takeaway to land

"What went wrong" is rarely a satisfying enough diagnosis on its own — it's almost always "which two of the four properties met here, and how." That question is cheap to ask and expensive to skip: the naive fix (ask the model to recheck itself) can fail repeatedly on a problem where the diagnosis-matched fix (route to real code execution) resolves it in one shot, verified. The four properties were never meant to be memorized in isolation — the payoff was always in naming the intersection.

## Exercise: The Failure Diagnosis

**Why:** turns "that wasn't quite right" into an actionable, targeted fix instead of a shrug.

1. Gather 3–4 real AI-output failures — your own past incidents if you have them, or freshly generated ones (a niche-topic citation request, a long back-and-forth where an early constraint got dropped, a hand-computed multi-step math problem, a pushback test on a correct-but-challenged answer).
2. For each one, name which one or two of the four properties (Next Token Prediction, Knowledge, Working Memory, Steerability) were actually in play — resist stopping at the first plausible-sounding diagnosis if a sharper one is available.
3. For each diagnosis, name the fix that actually matches it (reground in a source, restate the constraint, route to code execution, add a checkpoint) rather than a generic "ask it again."
4. If you can, test the fix and verify the result independently.
