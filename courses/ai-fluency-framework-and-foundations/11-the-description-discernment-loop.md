# The Description-Discernment loop

Parent: [Course overview](./README.md)
Previous: [A closer look at Discernment](./10-a-closer-look-at-discernment.md)
Next: [A closer look at Diligence](./12-a-closer-look-at-diligence.md)

No video — hands-on practice lesson, applying [A closer look at Description](./08-a-closer-look-at-description.md) and [A closer look at Discernment](./10-a-closer-look-at-discernment.md) together to the running project from [Project planning and Delegation](./07-project-planning-and-delegation.md).

## The point

Put everything learned so far into practice by actually executing the project planned earlier, using Description and Discernment as a repeated feedback loop rather than one-shot instructions.

## Structure of the exercise

**Step 1 — Review your project plan.** Pull up the plan, re-check the delegation decisions, refine if you've learned something since.

**Step 2 — Prepare your Description approach**, across the same three dimensions Discernment mirrors:
- *Product Description* — what specific outputs, in what format/style/length/detail?
- *Process Description* — how should Claude approach each task — specific methods, frameworks, steps?
- *Performance Description* — what collaborative behavior do you want — concise or detailed, challenging or supportive, idea-focused or analysis-focused?

**Step 3 — Execute using Description-Discernment loops**, per task:
1. Describe (Product/Process/Performance).
2. Discern the result (Product/Process/Performance Discernment).
3. Refine — give feedback on what worked/didn't, adjust the description, iterate.
4. Integrate your own expertise — add your perspective, make the final call on what to keep/modify/discard, take responsibility for the output.

Repeat per task until the project is done.

## Ties to the 4Ds

This is the lesson where Description and Discernment stop being separate topics and become one operating loop — "most AI interactions are small loops of Description and Discernment, describing what we need, evaluating what we get, refining our request" gets formalized and practiced here.

## How this connects to the companion course

The [AI Capabilities and Limitations](../ai-capabilities-and-limitations) course's [When Properties Collide](../ai-capabilities-and-limitations/08-when-properties-collide.md) lesson resolves failures by naming which two model properties are interacting and routing around them (e.g. a math failure resolved by routing to code execution rather than re-prompting blindly). The Description-Discernment loop is the general-purpose version of that same move for a human collaborator without deep model-internals knowledge: describe, evaluate, and specifically *refine the description* rather than just re-asking — which only works if the Discernment step correctly diagnosed *why* the output fell short (Product vs. Process vs. Performance), the same way the companion course insists on diagnosing *which* property failed before reaching for a fix.

## Key takeaway to land

Description and Discernment aren't sequential steps you do once each — they're a loop you run repeatedly per task, and the loop only improves outcomes if Discernment is specific enough (which dimension failed?) to produce a sharper Description on the next pass.

## Exercise: Project execution with Description-Discernment loops

**Why:** this is the first time the course asks you to run the full loop against something real and multi-step, rather than a single practice prompt.

1. Review and (if needed) refine your project plan from [Project planning and Delegation](./07-project-planning-and-delegation.md).
2. Set up Product/Process/Performance Description expectations with Claude before starting.
3. Work each task through the loop: describe → discern (Product/Process/Performance) → refine → integrate your own judgment.
4. Repeat until the project is complete.

### What running this loop for real tends to surface

Working through this repo's own AWS cheat sheet project through the loop surfaced a few patterns worth expecting in your own run:

- **Clear, specifically-bounded constraints outperform vague guidance.** A concrete, numeric constraint (e.g. "minimum 3, maximum 6 sources") tends to produce better outcomes than a qualitative instruction like "cite good sources" — matching [Effective prompting techniques](./09-effective-prompting-techniques.md)'s "specify constraints" advice, confirmed in practice rather than just in theory.
- **Which side costs more effort — Description or Discernment — is task-dependent, not universal.** A build-something task (a website, a document) tends to weight harder on Description (getting the spec right up front); domain-expertise research work tends to make verifying output accuracy (Discernment) the heavier lift.
- **Description iteration can retroactively improve your original Delegation-stage plan.** It's common for a project to start as a vague "let's build X" and end at a very specific templated output — the prompting/Description work feeding back into and sharpening the plan you made before you'd actually run the loop, rather than the textbook order (Delegation locked in, then Description executed against it) holding strictly.
