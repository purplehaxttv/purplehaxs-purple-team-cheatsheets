# Working Memory

Parent: [Course overview](./README.md)
Previous: [Knowledge](./05-knowledge.md)
Next: [Steerability](./07-steerability.md)

Taught by Matt, Anthropic user research team.

## The point

Everything sits inside one fixed-size workspace: instructions, prior responses, uploaded documents, the whole back-and-forth. **The model can only tend to what's inside.** Hard size limit — once exceeded, something falls off, usually the oldest material, usually silently. No announcement that the first three messages got dropped. By default the window empties between sessions entirely — a new chat starts from zero unless a product feature (memory, a project file) deliberately carried something forward.

## The cliff — the one property that doesn't degrade gradually

Same continuum framing as the other three properties (capability zone = fits comfortably, current session; limitation zone = long documents, long conversations, expecting recall from last week) — **but the shape is different.** Next token prediction thins out gradually. Knowledge gets sparser gradually. Working memory works right up until it doesn't, often with no warning. **While in the capability zone, context is genuine leverage** — upload a short style guide, ask for a draft, the model adapts immediately, no retraining, no setup, inside one session.

## Why it's fixed at all

The model processes the entire context as a single block, every single generation — reading all of it, start to finish, to decide what to write next. There's a ceiling on how much it can hold and still produce a coherent reply.

## Lost in the middle

Even inside the ceiling, attention isn't uniform. Material buried deep in a long input carries less weight than material at the beginning or end. Rapid in-session adaptation and precision-through-specificity are real — but placement inside the window matters, not just whether something technically fits.

## Product-level mitigations

- **Memory** — saves selected facts across sessions, avoids starting from zero every time.
- **Compaction/summarization** — condenses history to free room in a long-running conversation.
- **Projects/workspaces** — keep standing documents reliably in context without re-uploading.
- **Agent skills** — keep instructions minimal until a specific task actually needs them.
- **Multi-agent workflows** — multiple agents with their own context windows, expanding total available context for the workflow.
- **Larger context windows** — push the cliff further out; don't eliminate it.

## Signs you're approaching the edge

A long conversation where quality has started to slip. A long document where middle details stop showing up. Expecting recall from a prior session with no memory feature enabled.

## Techniques

- Lead with what matters — important material near the top, not buried on page 12.
- Chunk long work into passes rather than one giant upload.
- Use product features built to save context (projects, skills) instead of re-supplying by hand every time.
- **If quality degrades over a long conversation, start fresh rather than pushing through** — slippage is often a context limit, not a capability limit. A new chat with a short summary can outperform continuing.

## Ties to the 4Ds

Working memory is the mechanism that makes **Description** work at all — every instruction, constraint, and example only has effect if it's actually inside the window. Understanding size, edges, and reset behavior is what tells you when to restate critical context and what's actually worth uploading.

## A real, worked example: two probes, one confirming, one that came back empty

Two structural tests are worth running to actually feel where the cliff is, rather than just knowing it's there:

**The blank-slate test.** Teach the model something specific in one conversation (a made-up preference, a project codename). Then, in a brand-new conversation with zero prior turns included, ask about it. The correct, well-calibrated response isn't a confabulated guess — it's the model correctly identifying it has no basis for an answer and asking for the information again. That's the reset behavior working exactly as described, paired with good calibration about its own blank state.

**The lost-in-the-middle test.** Build a moderately long document (a few hundred words), bury one important instruction in the middle, ask a question that depends on catching it. Move the same instruction to the top, ask again, compare. Worth logging honestly: at short lengths, this effect can fail to show up at all — a real negative result, not a failed test. "Lost in the middle" is scale-dependent, not purely positional. A document that isn't long enough simply doesn't stress the mechanism — the effect is much easier to find at real scale (tens of thousands of tokens), not a few hundred words.

**The sharpest gap tends to show up in a cold-start-vs-context test.** Ask for a piece of writing in a specific house style with zero examples given, then ask again in a fresh conversation with one real example of that style pasted in first. The jump in structural accuracy from the first to the second is often dramatic — going from generic default formatting to something close to indistinguishable from the real style, off a single example. Worth watching for the failure mode that comes with it, though: the model can learn a *pattern* (say, a specific link structure) perfectly while fabricating the actual *content* of that pattern (an invented-but-plausible link target) — the same "specificity is where fabrication concentrates" finding from [Next Token Prediction](./04-next-token-prediction.md), surfacing in a structural task instead of a factual one.

## Key takeaway to land

Context is leverage right up until it isn't, and the transition doesn't announce itself. The fix isn't a bigger window (that just moves the cliff) — it's structural habits that don't depend on trusting what's sitting in the middle: lead with what matters, re-supply what's critical, and treat "quality just dropped" as a context signal to investigate before assuming it's a capability one.

## Exercise: The Before-and-After

**Why:** context is leverage — this makes that concrete, going from mediocre first draft to genuinely useful.

1. Pick a task that benefits from context only you hold (style guide, past example, role/audience-specific constraints). Write 2–3 lines defining "good" for this task's output, clear enough a stranger could evaluate it.
2. **Probe 1 — cold start vs. context.** Run the task with zero context, save it. Fresh conversation, same task, context supplied upfront. Compare both against your "good" definition.
3. **Probe 2 — lost in the middle.** Bury one important instruction in the middle of a longer document, ask a question depending on it. Did it catch it? Move the instruction to the top, ask again, compare.
4. **Probe 3 — the blank slate.** Teach the AI something specific, or correct it, in one conversation. Open a brand-new one, ask a question assuming it remembers. Watch it start from zero.
5. Tag your own real tasks a third time: needs standing context (project/saved instructions/uploaded docs) to be worth running, vs. works fine cold.
6. **Stretch goal:** set up memory/project features with Probe 1's context, rerun, compare effort/quality against cold-start.
