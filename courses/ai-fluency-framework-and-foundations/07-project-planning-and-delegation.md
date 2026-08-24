# Project planning and Delegation

Parent: [Course overview](./README.md)
Previous: [A closer look at Delegation](./06-a-closer-look-at-delegation.md)
Next: [A closer look at Description](./08-a-closer-look-at-description.md)

No video — this is a hands-on practice lesson, applying [A closer look at Delegation](./06-a-closer-look-at-delegation.md) to a real project.

## The point

Apply Delegation to a practical multi-step project you'll work on throughout the *rest of the course* — this project becomes the running example for Description, Discernment, and Diligence too. It's the course's spine exercise, not a one-off.

## Structure of the exercise

**Step 1 — Choose your project.** Medium-sized, multi-step, completable in ~1 hour of work, genuinely interesting to you. Suggested categories: Communication (presentation, explainer post, pitch, bio), Research (summarize an emerging trend, analyze a dataset, compare options, investigate a historical event), Creative (short story outline, website structure, product concept), Learning (structured learning plan, resource collection, tutorial, study materials).

**Step 2 — Project vision and goals.** Start a conversation with Claude, share the project idea, and let Claude ask questions until there's a solid vision: what success looks like, and what would make the project particularly valuable/meaningful.

**Step 3 — Task breakdown and delegation analysis.** Work with Claude through the Delegation lens: identify major tasks, then for each one discuss — what skills/knowledge/AI capabilities are needed, which parts favor human strengths, which favor AI, where collaboration has the most impact. Have a *genuine conversation*, not an exchange of statements — challenge assumptions, ask for clarification, stay open to unexpected insight. End with a saved project plan (major tasks + delegation decisions) to return to later for Description, Discernment, Diligence.

## Ties to the 4Ds

Pure Delegation practice — the whole exercise *is* the "what should I do vs. what should AI do" decision, applied for real instead of hypothetically. Explicitly sets up the next three competencies: the plan built here gets reused to practice Description, Discernment, and Diligence.

## Key takeaway to land

Delegation isn't graded in the abstract — this lesson forces a real decision about a real project, on the record, to be checked against what actually happens later in the course.

## Exercise: Choose and delegate-plan a real project

**Why:** turns Delegation from a concept into a standing commitment that the rest of the course holds you to.

1. Pick a project (see categories above) — medium scope, ~1 hour, genuinely interesting.
2. Have a real back-and-forth with Claude to nail down the vision and what success looks like.
3. Work through task breakdown + delegation analysis per task (human vs. AI vs. collaboration), as a genuine conversation, not a checklist exchange.
4. Save the resulting project plan — it's reused in later lessons.

### A worked example: this repo's own running project

This course's exercise is exactly how the [AWS Cloud Security Purple-Team Cheat Sheet](../../aws) in this repo got started — it's a real, published artifact, not a hypothetical.

**Vision:** a reference doc/cheat sheet covering common AWS cloud security vulnerabilities, purple-team style — exploit technique and mitigation presented side by side per vulnerability. Scope: AWS specifically, to start. Audience: built to a standard shareable with other security professionals.

**Task breakdown + delegation plan, one reasonable split:**

1. **Compile the vulnerability category list** (IAM misconfig, S3 exposure, overly permissive policies, exposed secrets, insecure Lambda/serverless, logging/monitoring gaps, VPC/network misconfig, encryption gaps, etc.) — AI drafts *with web search enabled*, human reviews for gaps/relevance from real experience.
2. **Document attack vectors** per category — AI drafts *with web search enabled* (the task most exposed to knowledge-cutoff staleness — exact technique/tooling names go out of date fast), human judges currency and accuracy.
3. **Document detection/mitigation** per category — AI drafts from training knowledge (a more stable domain than attack techniques), human reviews.
4. **Verify against current state** — human, or AI with web search explicitly enabled; pure recall is explicitly ruled out as the wrong tool for this task.
5. **Format for shareability** — AI drafts structure/layout, low-stakes to automate.
6. **Review for the "hand to other professionals" bar** — human only; judging what reads as credible to peers isn't something an AI system has visibility into.

The entry template that came out of iterating on this plan through Description and Discernment lives in [`aws/README.md`](../../aws/README.md) — worth reading alongside this lesson as the concrete "what the delegation plan actually produced" artifact.

## What to do with your own plan

Once you have a real project plan of your own, treat it the same way — carry it forward into [A closer look at Description](./08-a-closer-look-at-description.md) and beyond, refining the plan as you learn more rather than treating Delegation as a one-time, up-front decision you never revisit.
