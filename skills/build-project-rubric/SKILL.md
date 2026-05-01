---
name: build-project-rubric
description: Generate a project-specific QA/QC evaluation rubric the agent uses to self-evaluate work products before declaring them "done." Two-tier structure (first-principles + tactical) with project-specific criteria added based on the project's intent and curated research. Use after `curate-research-folder`. Trigger phrases include "build a rubric," "make the quality gate," "how will we know it's done," "quality criteria."
---

# build-project-rubric

## When to invoke
- After `clarify-intent` and `curate-research-folder` have run
- When `RUBRIC.md` is still placeholder content
- Whenever the user wants to formalize the quality bar for the project

## What this skill does

Generates a `RUBRIC.md` with three dimensions:

1. **First-principles tests** — does the work actually answer the question and serve the audience?
2. **Tactical-quality tests** — are the artifacts well-made (readable, sourced, accessible)?
3. **Project-specific criteria** — domain or audience considerations the agent and user discover during scoping

Each criterion is scored 0-4 with weights that sum to 100%. Disqualifying failure modes are listed separately.

## Steps

1. **Read `README.md`** for intent, audience, deliverable type, and constraints.
2. **Read `Research/README.md`** to identify domain-specific quality conventions.
3. **Draft Dimension 1 (first-principles)** — 3-5 criteria covering intent satisfaction, audience-fit, source integrity. Use the template starter and adapt to the project.
4. **Draft Dimension 2 (tactical)** — 3-5 criteria specific to the deliverable type:
   - For slides: rendering correctness, readability at 1280×720, WCAG AA contrast, citation discipline, glance test
   - For reports: structure, citation density, copy-edit quality, executive-summary accuracy
   - For code: tests pass, lint clean, security scan clean, docstrings present, complexity bounds
   - For analyses: data lineage, methodology documentation, reproducibility, sensitivity analysis
5. **Draft Dimension 3 (project-specific)** — start empty or with 1-2 criteria the user names explicitly. This dimension grows during the project as failure modes are discovered.
6. **Set weights** so the dimensions sum to 100%. Default: D1 = 40%, D2 = 40%, D3 = 20%. Adjust based on project specifics.
7. **List disqualifiers** — any criterion at 0 that should permanently block ship.
8. **Write `RUBRIC.md`** with full table format and scoring template.
9. **Append a structured entry to `LOG.md`** documenting the rubric creation.

## Scoring scale

- **4 — Exemplary**: this criterion is itself a reason the work will be remembered
- **3 — Strong**: clearly meets the bar; minor polish only
- **2 — Adequate**: serviceable; would not embarrass but does not win
- **1 — Weak**: meaningful problem; the audience will notice
- **0 — Disqualifying**: cannot ship until resolved

## What NOT to do

- Do not write a generic "best practices" rubric. The rubric is project-specific. Generic rubrics catch nothing.
- Do not include criteria the agent or user can't actually evaluate. If a criterion requires data the agent doesn't have access to, drop it or replace it.
- Do not lock the rubric. It's a living document that grows as the project surfaces new failure modes.
- Do not allow the rubric to balloon. 8-12 criteria is a healthy total. More than 15 dilutes the focus.

## Output format

```
==> RUBRIC.md created with <N> criteria across 3 dimensions.

  Dimension 1 (first-principles): <count> criteria, <weight>%
  Dimension 2 (tactical): <count> criteria, <weight>%
  Dimension 3 (project-specific): <count> criteria, <weight>%

  Disqualifiers: <list>

==> Logged in LOG.md.
==> The rubric is now active. The agent will self-evaluate against
    it before declaring any work product ready.
==> When you discover new failure modes, add them to Dimension 3.
```

## Operating principles

- **Specific beats generic.** A rubric criterion that names a concrete failure mode catches it; one that names a vague aspiration doesn't.
- **Living, not locked.** Add criteria as you discover them. The third dimension is designed to grow.
- **Disqualifiers are non-negotiable.** Any 0 stops shipment regardless of other scores. This catches the "everything else is fine but this one thing breaks the whole work" failure mode.
