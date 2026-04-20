---
name: Don't telegraph infrastructure in public content
description: In blog posts, LinkedIn, and any public content, don't name where inference runs (local server, on-prem hardware, specific cloud). Keep deployment generic.
type: feedback
---

Don't state "we run locally", "on-prem hardware", "in-house GPUs", or any specific detail about where inference runs in public content (blog posts, LinkedIn posts, etc.). Frame the pipeline as deployment-agnostic: BYOM (Bring Your Own Model), deploys wherever fits the customer's setup.

**Why:** David's position: "we dont want to make easier hakers life right?" Publishing where critical inference lives is an information leak that narrows the attack surface for someone looking to target a running deployment. Also, clients have different deployment preferences (on-prem, cloud, hybrid), and committing publicly to one framing limits commercial flexibility.

**How to apply:**
- When describing cost efficiency in the inference section, frame it as "using a small fast model" instead of "running it on local hardware"
- When explaining flexibility, use "bring your own model, deploy wherever fits your setup" rather than naming specific infrastructure
- If talking about data residency, frame it as a property the pipeline supports rather than as a statement about where it currently runs
- Applies to all public-facing writing: blog posts, LinkedIn posts, demos, README files
