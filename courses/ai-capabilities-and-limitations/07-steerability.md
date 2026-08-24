# Steerability

Parent: [Course overview](./README.md)
Previous: [Working Memory](./06-working-memory.md)
Next: [When Properties Collide](./08-when-properties-collide.md)

Taught by Matt, Anthropic user research team.

## In this lesson

- Explain why steerability works (fine-tuning taught the model instruction-following) and why it has limits (instructions are followed via pattern-matching, not understanding).
- Predict where control is tightest (short, concrete, verifiable instructions) versus loosest (long reasoning chains, abstract asks, native precision tasks).
- Identify reasoning drift, letter-over-spirit, and instructions-as-attack-surface as characteristic steerability failures.
- Recognize system prompts, code execution, visible reasoning, and structured outputs as product features addressing this limitation.

## The point

Steerability is the model's ability to follow your directions — say "respond as a table" and you get a table, specify a role or tone and it shifts. **This isn't automatic.** A pre-trained model is a document completer with no concept of helping; [Pretraining and Fine-tuning](./03-pretraining-and-fine-tuning.md) is what teaches it to treat your text as a request, break tasks into steps, and apply rules. But steerability isn't understanding — the model follows instructions through the same pattern-completion engine it uses for everything else. There's always a gap between the words typed and the intent behind them, and **most interesting AI limitations live in that gap.**

## The live demo — "make it punchy"

Instruction: *"Summarize this report in under 100 words and make it punchy."* Result: exactly 100 words, genuinely punchy — and the one qualified finding that actually mattered got cut to make room. **The instruction was honored to the letter; the intent was missed.** This is letter-over-spirit, live, not hypothetical.

## The continuum

- **Capability zone** — short, concrete, verifiable: respond as a table, under 100 words, an exact schema. Simple to pattern-match, checkable at a glance.
- **Limitation zone** — long reasoning chains (a small error in step 2 quietly carries through 3, 4, 5), vague asks ("be insightful") where the model has to guess intent, anything needing native numeric or logical precision.
- **The reframe:** not "did I write a good prompt," but **"how much room is there between what I typed and what I actually want?"**

## What the capability zone actually buys you

- Tight control over format and style.
- A persona held across the whole conversation.
- Multi-step task execution when the process is laid out explicitly.
- Iterative refinement — "shorter," "more formal," "try the opposite angle" — all land cleanly.

## The characteristic failures

1. **Reasoning drift** — a small error early in a long chain compounds silently through later steps, uncaught.
2. **Letter-over-spirit** — the instruction is honored literally but lands uselessly (the "make it punchy" demo).
3. **Instructions as an attack surface** — because the model follows instructions embedded in *any* text, a malicious instruction hidden inside a document or webpage can be followed just as readily as one typed by the user. Known as **prompt injection** — more a security concern than a daily one, but worth knowing exists.

## Product-level mitigations

- **System prompts / custom instructions** — standing directions that don't dilute as the conversation gets longer.
- **Extended/visible reasoning** — catches drift at step two instead of only in the final answer.
- **Structured output modes** (JSON schemas, function calling) — narrow the room for letter-over-spirit wandering.
- **Code execution** — routes native-precision tasks to something that actually computes, instead of asking the pattern-completion engine to do arithmetic by feel.

## Techniques

- **State the goal alongside the steps.** "I'm trying to persuade a skeptical audience" gives the model more to work with than a format spec alone.
- **Break long chains with checkpoints.** Ask for an intermediate, verifiable result before the model keeps going.
- **When an instruction lands literally but uselessly, restate the goal, not the instruction louder.** "Be concise" said again doesn't fix an intent problem.
- **Keep concrete, verifiable instructions near the task.** Short and checkable beats long and ambiguous.

## Ties to the 4Ds

Steerability is both what **Description** exploits and what bounds it — good description narrows the gap between your words and your intent. It shapes **Delegation** too: tasks needing long reasoning chains or native numeric precision need either tighter human checkpoints or a different tool entirely.

## A real, worked example: checkpoints changing the failure profile, not just the score

A useful way to feel reasoning drift directly: give a multi-step diagnostic chain (5+ steps), pre-seed that the obvious first checks are already done (to force the model past easy answers into a real chain), and compare two runs — one with no checkpoint, one where you stop the model partway and ask it to state what it's confirmed vs. what still needs verifying.

**No checkpoint:** the model tends to run all steps straight through and close with a single confident conclusion, bundling several unverified hypotheses together as if they'd all been checked, when nothing was actually confirmed against real ground truth.

**Checkpoint after an early step:** the model tends to stop and explicitly separate *"here's what I'd check"* from *"here's what needs confirming before I go further,"* naming the specific facts that would need verifying — rather than silently building further reasoning on an unchecked assumption.

The checkpoint version doesn't necessarily produce a "better" answer on the first pass — it produces an *honest* one, by refusing to silently compound an unverified assumption into a confident final conclusion. That's the checkpoint technique demonstrated rather than just asserted.

A second useful test, for letter-over-spirit: bury one load-bearing caveat in a short paragraph, then ask for a summary under a strict word count with a tone instruction ("make it punchy"). Sometimes the caveat survives compression; sometimes it doesn't — and that inconsistency is the actual finding. A bare word-count-and-tone instruction gives the model nothing to signal *which* detail is load-bearing, so whether the important part survives is closer to a coin flip than a guarantee. Stating the goal explicitly ("compress this, but the caveat about X must survive") converts that coin flip into something closer to a guarantee.

## Key takeaway to land

The model will follow you — reliably, on the first try, most of the time. The gap that remains isn't a reliability problem you fix by saying the same instruction louder; it's a *translation* problem between what you typed and what you meant, and it widens exactly where chains get long, asks get abstract, or precision gets native. Your job isn't writing a better-worded instruction — it's noticing how much room that gap has on this specific task, and closing it with a goal statement, a checkpoint, or a structured format, whichever the gap actually calls for.

## Exercise: The Goal Rewrite

**Why:** the gap between what you say and what you mean is where most steerability failures live. This exercise teaches you to prompt from intent, not just from instruction.

1. Pick a real multi-step task you've delegated to AI before — ideally one that had to be run more than once to get right.
2. **Probe 1 — Tight control.** Give a short, concrete instruction with an exact, checkable format ("respond with a numbered list of exactly 3 steps and nothing else"). Confirm it holds precisely.
3. **Probe 2 — Reasoning drift.** Give a 5+ step diagnostic or reasoning chain. Run it once straight through, then run an equivalent version where you insert a checkpoint partway and ask the model to state what's confirmed vs. what still needs checking. Compare the two closing conclusions.
4. **Probe 3 — Letter vs. spirit.** Write a short paragraph with one buried, load-bearing detail. Ask for a strict-word-count, tone-shaped summary ("make it punchy"). Did the load-bearing detail survive?
5. Write a goal statement (not just a format spec) for a recurring task of yours, and note where in the task a checkpoint would be cheap to add.
