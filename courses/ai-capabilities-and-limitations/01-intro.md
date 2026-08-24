# Intro to AI Capabilities and Limitations

Parent: [Course overview](./README.md)
Next: [What we mean by AI](./02-what-we-mean-by-ai.md)

## The point

The [4Ds](../ai-fluency-framework-and-foundations/03-the-4d-framework.md) (Delegation, Description, Discernment, Diligence) are the *human* side of AI collaboration — what you do. This course is the *machine* side — what the model does when prompted, and why. You can't delegate well without knowing where the model is strong or weak, and you can't discern output quality without a picture of how that output got produced.

The two frameworks click together directly:
- Understanding AI as a **prediction engine** changes how you *describe* tasks.
- Understanding the **context window** changes how you *delegate* long tasks.

## Why this course is built to not go stale

Models change constantly — context windows grow, hallucination rates drop, features ship monthly. The course deliberately teaches the *shape* of the underlying properties, not current numbers:

- Next token prediction will still be next token prediction next year.
- The knowledge cutoff will move, but there will always be one.
- The context window will get bigger, but it'll still be an edge you can hit.

## Roadmap

1. **Two training stages** and the fingerprint each leaves on model behavior:
   - Pre-training → builds a document completer
   - Fine-tuning → shapes that into an assistant
2. **Four core properties**, each treated as a continuum (not a yes/no) to place a given task on:
   - Next token prediction
   - Knowledge
   - Working memory
   - Steerability
3. **Interconnections** — most real failures are two properties meeting at once:
   - Hallucinated citation = next token prediction × a knowledge gap
   - Drift over a long conversation = working memory × steerability
   - Naming the combination tells you *why* it happened and *what to do about it*.

## How to actually do the exercises

Don't use generic examples — bring real tasks, in a domain where you're expert enough to notice when something's off:
- Working memory section → load your own long documents
- Next token prediction section → ask about your own niche topics

The goal is calibration you can *feel*, not a glossary you memorize.

## Exercise: Mapping Your Current AI Use

**Why:** foundation for every exercise in the rest of the course — revisit this same list each lesson and watch it change.

1. List 4–6 tasks you've actually done with AI in the last two weeks (or wanted-to tasks, if you're light on AI use so far). Be specific — "drafted a client email explaining a project delay," not "writing."
2. For each: one line — did it land first try, or need rework? Gut check, don't overthink.
3. Share the list with your AI assistant: *"For each of these tasks, what's one way this could go wrong if I'm not paying attention?"* Check whether the failure modes named feel relatable. If not, push back: *"That doesn't match my experience. Here's what actually went wrong..."*

**Worth watching for as you build the list:** tasks that are *tool-grounded* (real file reads, real command output, real web fetches) tend to be much safer than tasks that ask the model to generate from pure recall with nothing to check it against. That distinction — grounded vs. ungrounded — predicts which of the four properties (covered in the coming lessons) is even in play, before you get into specifics.

**A useful second pass, once you've listed the tasks:** for each one, ask whether a wrong output would touch something *live/irreversible* (real credentials, a public claim about a real person, a production system) or something *local/undoable* (a draft you can just rewrite). That axis — not task complexity — is usually the better predictor of how much verification a task actually needs.

## Key takeaway to land

This course explains the *machine* half of AI collaboration the way the 4Ds explain the *human* half. Everything downstream (pre-training vs. fine-tuning, the four properties, their intersections) is in service of one thing: being able to look at a weird AI output and immediately name which property (or combination) produced it.
