# Purplehax's Purple Team Cheat Sheets

A growing collection of security cheat sheets, purple-team style — every entry pairs the attack (how it's actually exploited) with the mitigation (how to lock it down), instead of picking one side.

Built the way this content should be built: search-first rather than relying on model recall, verified against 3-6 independent sources per entry (official docs first, professional research second, individual researcher content last), with contested claims flagged inline instead of smoothed over. Written to be technically accurate but still readable if you're newer to the domain — not gatekept behind jargon.

Grown out of live Twitch prep work, not written cold — see the AWS section for the first entries.

## Coverage

- [`aws/`](./aws) — AWS cloud security: IAM, S3, more to come.
- More cloud/security domains added here as they're built.

## Courses

Lesson-by-lesson companion notes for two Anthropic Claude Academy courses — kept here because the AWS cheat sheet above started life as the running project for one of them.

- [`courses/ai-fluency-framework-and-foundations/`](./courses/ai-fluency-framework-and-foundations) — the 4D framework (Delegation, Description, Discernment, Diligence) for collaborating with AI effectively, efficiently, ethically, and safely.
- [`courses/ai-capabilities-and-limitations/`](./courses/ai-capabilities-and-limitations) — the companion course covering what a model is actually doing under the hood (next-token prediction, knowledge, working memory, steerability) and why that shapes how well the 4Ds work in practice.

## A note on severity ratings

Where a cheat sheet entry includes a severity rating, it's meant to be a collaborative call (CVSS score + reasoning, discussed before finalizing), not something generated unilaterally. If you see an entry marked "pending," that's why — it hasn't gone through that step yet.
