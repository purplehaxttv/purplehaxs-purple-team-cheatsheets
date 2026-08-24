# Effective prompting techniques

Parent: [Course overview](./README.md)
Previous: [A closer look at Description](./08-a-closer-look-at-description.md)
Next: [A closer look at Discernment](./10-a-closer-look-at-discernment.md)

## The point

Prompt engineering is "simply the practice of designing effective instructions for AI systems" — combining ordinary human communication principles with AI-specific considerations. Six foundational techniques, plus a "secret weapon."

## Six foundational prompting techniques (as stated)

1. **Give context** — be specific about what you want, why, and relevant background. Worked example: "Tell me about climate change" upgraded step by step to "Explain three major impacts of climate change on agriculture in tropical regions with examples from the past decade. I'm preparing for a job interview at an agricultural research lab in Indonesia. I have a degree in ecology, but no specific knowledge on climate change..." — the *why* and *who you are* sharpen the answer as much as the *what*.
2. **Show examples** (few-shot/n-shot prompting) — demonstrate the output style/format you want, especially when a style is easier to show than describe. Try without examples first; add them only once you have a specific style that's hard to explain in words. Cover the *diversity* of cases you want, not just one example.
3. **Specify constraints** — format, length, language/framework, even literal details like button color on a requested webpage.
4. **Break complex tasks into steps** ("chain of thought prompting") — list out the steps you want followed, the same way you'd give a friend explicit instructions rather than assume they'll do it your way. Modern reasoning/extended-thinking models increasingly do step-by-step reasoning on their own, but you can still guide it. The more the task depends on domain expertise or has many valid approaches, the more worth doing this.
5. **Ask the AI to think first** — give it space to work through its process *before* answering, not explain its reasoning after the fact ("having space to think before you act is different than acting first, then being asked to explain your thinking afterwards"). Side benefit: seeing the thinking shows you where to sharpen your Description next time.
6. **Define the AI's role or tone** — who do you want the AI to act as (an experienced teacher explaining to a curious 10-year-old; a UX design expert reviewing a wireframe)? Shapes both the interaction style and the substance of the output.

**The "secret weapon":** ask the AI itself to help craft or improve your prompt when you're not sure how to ask — this is one of the areas where different AI systems/models vary most, worth experimenting with as part of Delegation (Platform Awareness).

Prompting is iterative and experimental — first attempts won't always be perfect, and that's expected. Concrete refinement moves: add specificity/context, provide examples, break into smaller steps, ask for variations ("give me three different versions"), request a different format, check confidence on factual claims ("how confident are you about this answer?"), or just reset to a fresh conversation rather than trying to correct one that's drifted. Common mistakes: assuming the AI can read your mind, overloading one prompt with unrelated tasks, being vague about what success looks like, not giving feedback on prior responses.

## Ties to the 4Ds

This is the practical, technique-level layer directly underneath [A closer look at Description](./08-a-closer-look-at-description.md) — Discernment addresses "the other half of the conversation" (evaluating what comes back), while this lesson and Description together cover the communicating-in half.

## How this connects to the companion course

The [Capabilities and limitations](./05-capabilities-and-limitations.md) lesson notes that newer "reasoning"/extended-thinking models specifically designed to think step-by-step show real improvement on multi-step problems — and the [AI Capabilities and Limitations](../ai-capabilities-and-limitations) course's [When Properties Collide](../ai-capabilities-and-limitations/08-when-properties-collide.md) resolves a live math failure by routing to code execution rather than trusting default generation. Technique #5 here ("ask the AI to think first") is the lightweight, no-tooling version of that same fix — worth testing directly: does explicitly asking for step-by-step reasoning meaningfully reduce errors on the kind of multi-step task that companion lesson describes, without needing to route to a different tool entirely?

## Key takeaway to land

None of the six techniques is exotic — they're closer to "how you'd brief a new colleague" than to a technical trick, and the explicit framing (prompting is iterative and collaborative) argues against treating any single prompt as something to get perfect on the first try.

## Exercise

No new named exercise on this page — it explicitly points back to reuse [A closer look at Description](./08-a-closer-look-at-description.md)'s "Bad Prompt Makeover" exercise as practice for these six techniques. As you run it, notice whether you tend to compress a genuinely multi-step task into one dense prompt instead of breaking it into steps (technique #4) — a consolidated ask like that also tends to leave less room to specify Performance (how the AI should behave along the way), so the two gaps often show up together.
