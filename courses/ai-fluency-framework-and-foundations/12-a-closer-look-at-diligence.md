# A closer look at Diligence

Parent: [Course overview](./README.md)
Previous: [The Description-Discernment loop](./11-the-description-discernment-loop.md)
Next: [Conclusion](./13-conclusion.md)

## The point

While Delegation, Description, and Discernment mostly serve *effectiveness and efficiency*, Diligence is the competency that covers *ethics and safety* — equally crucial, different axis. Framed with a driving analogy: getting from A to B efficiently isn't the whole job — you also follow traffic rules and stay aware of how your driving affects others. AI collaboration doesn't happen in a vacuum either.

## The three components of Diligence

- **Creation Diligence** — being critical and intentional about *which* AI systems you choose and *how* you work with them: how is the system trained, what data was used, who owns/can access what you input, how are you protecting privacy/security, does this align with your values or your org's policies?
- **Transparency Diligence** — being open about AI's role in your work with everyone who needs to know. Not just compliance — "maintaining trust and respect": people have a right to know when AI played a significant role in content or decisions affecting them. Different contexts (personal/academic/professional) carry different disclosure expectations, but the responsibility to figure out and meet them is on you.
- **Deployment Diligence** — taking informed responsibility for outputs you use or share: verifying facts, checking for bias, confirming usage rights, standing behind the result the same way you would if you'd written it entirely yourself. Explicit example: a journalist using AI to draft an article still has to verify every fact and source before publishing, to the same standard as if they wrote it unassisted.

## Ties to the 4Ds

This is the full Diligence lesson — the ethics/safety half of AI Fluency, distinct from the effectiveness/efficiency work of the other three Ds. Directly hands off into the exercise below: draft a **diligence statement** for your own running project.

## How this connects to the companion course

The [AI Capabilities and Limitations](../ai-capabilities-and-limitations) course's [Next Token Prediction](../ai-capabilities-and-limitations/04-next-token-prediction.md) lesson establishes that fluent output and *correct* output are not the same thing — a model can generate a confident, well-formed, wrong answer. Deployment Diligence ("verifying facts... so that you can stand behind what you share") is the explicit human countermeasure to exactly that risk. Diligence isn't a separate ethics bolt-on — it's the practical response to a mechanism the companion course already explains.

## Key takeaway to land

Diligence is the one D that isn't about getting a better result faster — it's the acknowledgment that *you*, not the AI, are accountable for whatever you ship, and that accountability has to be established deliberately (choice of system, disclosure, verification) rather than assumed by default.

## Exercise: Creating a Diligence Statement

**Why:** turns "take responsibility for AI-assisted work" from an abstract principle into a concrete artifact attached to your actual project.

1. **Understand diligence statements** — a transparent acknowledgment of AI's role plus a commitment to responsibility for the final output. Example form: "In creating this [document/project], I collaborated with [AI assistant] to assist with [tasks]... I maintain full responsibility for the content, its accuracy, and its presentation."
2. **Reflect on your AI collaboration** across all three Diligence types — Creation (which systems, what data shared, privacy/ethics considerations), Transparency (who's the audience, what disclosure do they expect, how specifically did AI contribute), Deployment (how did you verify accuracy, how did you ensure it meets your standards, what responsibility are you taking).
3. **Draft the statement with Claude** — share your Step 2 reflections, collaborate on a statement covering which AI systems, how they contributed, your review process, your assertion of responsibility, and any context-specific considerations.
4. **Add the statement to your project** — footer, appendix, or metadata.

### A worked example: this repo's own diligence statement

The [AWS Cloud Security Purple-Team Cheat Sheet](../../aws) in this repo carries a real diligence statement, drafted through exactly this exercise:

> In creating this AWS Cloud Security Purple-Team Cheat Sheet, the author collaborated with Claude (Anthropic) to research, draft, and structure content covering common AWS vulnerabilities, attack vectors, and mitigations.
>
> **Creation:** Content generation used web search rather than model recall alone, specifically to reduce the risk of stale or outdated technical claims — verified against a minimum of 3 and maximum of 6 sources per entry, prioritizing AWS official documentation first, professional security research second, individual researcher content last.
>
> **Transparency:** This document is built for a professional security audience but written to remain accessible to entry-level readers; contested or disputed claims are flagged inline with a cited counter-source rather than presented as settled fact.
>
> **Deployment:** Severity ratings and cross-service attack-path claims were treated as collaborative checkpoints, not autonomous AI output — reviewed and discussed before being finalized, not accepted by default. The author takes responsibility for the technical accuracy of this document and its fitness for use by other security professionals; AI assistance was instrumental in producing it, but the author stands behind the final content.

Worth noticing: most of the substance in a statement like this (source-priority rules, contested-claim flagging, consultation checkpoints) tends to already be running as practice *before* you formally sit down to write the statement — the exercise mostly documents Diligence you were already doing, rather than introducing brand-new behavior.

## A genuine trade-off worth naming honestly

Transparency about AI's role does build trust with an audience that values it — but in the current environment, disclosing the extent of AI's involvement can also cost you some of the audience that doesn't want to engage with AI-assisted work at all. That's a real cost, not a hypothetical one, and it's worth accepting deliberately rather than being surprised by it after the fact — it's a consequence of the broader landscape (inconsistent norms and disclosure practices across the field generally) rather than a reason to hide your own use. As long as those underlying industry-wide questions (training-data consent, disclosure norms) stay unresolved, this reputational cost to honest individual disclosure is likely to keep being real. Diligence doesn't promise the trade-off disappears — it just insists you make the call deliberately instead of by default.
