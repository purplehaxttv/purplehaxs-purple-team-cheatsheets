# A closer look at Description

Parent: [Course overview](./README.md)
Previous: [Project planning and Delegation](./07-project-planning-and-delegation.md)
Next: [Effective prompting techniques](./09-effective-prompting-techniques.md)

## The point

"AI can't read your mind." Description is the competency of communicating with AI — not "clever prompts," but building a bridge between your intentions and the AI's capabilities. Central analogy: asking someone to "make dinner" vs. handing them a detailed recipe with ingredients and instructions.

## The three types of Description

- **Product Description** — clearly defining *what* you want the AI to create or provide: context, exact task, output format, audience, appropriate style. Don't make AI guess what you're thinking.
- **Process Description** — guiding *how* the AI approaches the request, sometimes as important as the end goal itself. Approaches: general guidance (like a manual), step-by-step instructions (like a cookbook), or demonstration through examples ("here's how I'd do it"). Includes specifying what data to draw on, what order to address issues in, what analysis style or workflow to use.
- **Performance Description** — defining the *behavioral* aspects of the interaction: narrowing to one answer vs. exploring possibilities, challenging your assumptions vs. following your lead, expansive detail vs. concise, explaining its reasoning vs. just answering. Central framing, called out as the course's single most important point: "AI tools are not databases or vending machines. They are interactive systems that can behave differently in different contexts, much like people might."

## Ties to the 4Ds

This is the full Description lesson, second D, directly setting up its counterpart [A closer look at Discernment](./10-a-closer-look-at-discernment.md) (Product/Process/Performance mirrored on the evaluation side) and feeding into [The Description-Discernment loop](./11-the-description-discernment-loop.md) where both get applied together to a running project.

## How this connects to the companion course

Performance Description ("explain how you want the AI to behave") is the direct practical application of what the [AI Capabilities and Limitations](../ai-capabilities-and-limitations) course's [Steerability](../ai-capabilities-and-limitations/07-steerability.md) lesson explains mechanistically: instruction-following as pattern-completion, where the model extrapolates from the *shape* of your guidance. If steerability is inherently imperfect, Performance Description is the mitigation — being explicit about behavior rather than assuming the model will infer the right register from context alone.

## Key takeaway to land

Product, Process, and Performance aren't three optional add-ons to a prompt — they're three separate questions ("what," "how," "how should you act while doing it") that a vague prompt leaves the AI to guess at, and guessing is where results drift from what you actually needed.

## Exercise: Bad Prompt Makeover

**Why:** trains the instinct to spot *which* Description dimension a weak prompt is missing, by deliberately practicing on bad examples instead of writing from scratch.

1. Ask Claude to challenge you with poorly written prompts.
2. Improve each one using all three Description types: clear Product (what exactly), Process guidance (how to approach it), Performance specifications (how Claude should behave during the collaboration).
3. Discuss before/after versions with Claude and get feedback on your improved descriptions.
4. After ~5 minutes, switch roles — you write bad prompts, Claude fixes them. Notice what information mattered most for clarity.

A useful way to see this land concretely: take a genuinely vague starting prompt like "Write something about my project" and rewrite it into a fully-specified version — audience, tone, citation requirements (Product), plus a note on whether web search or another tool should be used for accuracy (Process). Then trade roles and rewrite a similarly vague prompt like "Tell me about [broad topic]" into something scoped, sourced, and format-constrained. Across most people who run this, **Performance is the dimension most often left out entirely** — Product (what to produce) and Process (how to approach it) get specified fairly instinctively, but how the AI should *behave* during the interaction (concise vs. thorough, challenging vs. supportive) tends to go unstated, then gets blamed on the output being "not quite right" when the real gap was upstream.
