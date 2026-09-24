# Skills mined from `2026-Q1-MBA-Moderna-case`

*Generated 2026-05-13. Surveyed: LOG.md (47 entries), LESSONS_LEARNED.md (12 lessons), README.md, RUBRIC.md, Research/ (8 sources), work products (1 case deck, 1 teaching note, 1 student handout), humanizer-runs/ (6 logs). Existing skills checked: system-wide (4), project-local (0).*

## Summary

- HIGH priority: 2
- MEDIUM priority: 2
- LOW priority: 1
- Refused (single-occurrence or domain-specific): 2
- Already installed (skipped): 1

---

## Build first — HIGH priority

### #1 (HIGH · system-wide) · `source-citation-check`

**Lesson sources.** LESSONS_LEARNED.md #4 ("Caught a fabricated McKinsey citation in draft 3 of the teaching note — Claude inferred a source from the framing rather than verifying"), #7 ("Same issue showed up in the case deck — a 73% statistic with no source"), #11 ("Final round: had to re-verify every external claim. Took ~90 minutes."). LOG.md entries 2026-03-04, 2026-03-11, 2026-03-19 all show citation-rewrite cycles.

**Recurrence count.** 3 distinct lessons, 4 LOG entries, across 2 work products.

**ROI estimate.** Would have saved ~90 minutes of manual verification on this project alone. Every consulting memo and teaching artifact has this risk. Pairs well with `humanizer`'s no-fabrication rule.

**Placement.** System-wide. Citation hygiene is universal across consulting, teaching, and writing work; not domain-specific.

**Draft SKILL.md.**

```yaml
---
name: source-citation-check
description: Scans a draft for vague attributions ("studies show", "experts argue", percentages, named institutions) and asks the user whether each one has a real source. Keeps citations with verification; flags or removes those without. Use before publishing or sharing a draft with external attribution risk.
when_to_use: Trigger phrases include "check citations", "verify sources", "vet attributions", "audit the claims", "before publishing", "ready to ship this draft".
allowed-tools: Read AskUserQuestion Edit
---
```

Workflow:
1. Read the draft. Build a list of every attribution claim, every percentage, every named source.
2. For each: ask the user — do you have a real source? If yes, capture it. If no, ask: cut, soften, or leave as-is?
3. Apply the user's choice. Don't fabricate.
4. Output a citation log alongside the draft.

This is `humanizer`'s "no fabrication" rule extracted into a dedicated pre-publish gate.

---

### #2 (HIGH · system-wide) · `clarify-intent`

**Lesson sources.** LESSONS_LEARNED.md #1 ("Lost 2 days early because I didn't specify audience — Claude wrote for MBA students when the deck was for the visiting executive guest. Re-did the entire framing."), #2 ("Same failure mode on the handout — wrote at the wrong level of detail."), #9 ("By project 3 I started running an intent interview before letting any agent work. Should have done this on day 1.").

**Recurrence count.** 3 lessons, all upstream of cost. This is the user's own #1 cause of wasted agent work per their methodology repo.

**ROI estimate.** Saves the largest single category of rework: misaligned-deliverable rework. The user's own method explicitly identifies "skipping intent" as the most expensive shortcut.

**Placement.** System-wide. Already in the candidate-skills-backlog as Tier 1; this run confirms the recurrence signal is strong enough to promote.

**Draft SKILL.md.** Use the upstream from `leifulstrup/agentic-knowledge-work-method/skills/clarify-intent/SKILL.md` as a starting point. Modernize the frontmatter (add `when_to_use`, tighten `allowed-tools`) per the same protocol used for `humanizer` and `mine-skills-from-project`.

---

## Build next 2–3 projects — MEDIUM priority

### #3 (MEDIUM · project-local) · `mba-case-slide-template`

**Lesson sources.** LOG.md entries 2026-02-12, 2026-02-19, 2026-03-02 all show iterations on the same two-column "claim / evidence" slide layout. LESSONS_LEARNED.md #6 ("Settled on a stable two-column comparison slide format after 5 iterations").

**Recurrence count.** Pattern recurred on 5 slides within this case; will recur on every MBA case the user teaches.

**ROI estimate.** Saves ~15 minutes per slide on layout decisions; ~30 minutes per case on consistency review.

**Placement.** Project-local to MBA case projects. Not a general consulting need.

Better as a template snippet (just a markdown layout + a Keynote/Slides file) than as an agentic skill. Recommend storing in `~/Documents/Claude/MBA-templates/` rather than `.claude/skills/`.

---

### #4 (MEDIUM · project-local) · `teaching-note-outline`

**Lesson sources.** LESSONS_LEARNED.md #8 ("Teaching note structure: hook, dilemma, analytical frames, discussion questions, board plan. I rebuilt this from memory three times."). LOG.md 2026-02-28, 2026-03-15.

**Recurrence count.** 2 LOG entries, 1 explicit lesson; recurs every case taught.

**ROI estimate.** Modest. Saves the setup time but the content is always custom.

**Placement.** Project-local or template. Same logic as #3.

---

## Backlog — LOW priority

### #5 (LOW · project-local) · `case-reading-load-estimator`

**Lesson sources.** LESSONS_LEARNED.md #12 ("Overshot student reading load by 40% — had to cut readings the night before class").

**Recurrence count.** 1 lesson, 0 LOG entries. Single occurrence.

**Placement.** LOW because the recurrence signal is weak (one lesson). Logging this so it's not forgotten; not promoting unless it recurs on the next case.

This is the kind of candidate the operating principles warn about — one occurrence is a log entry, not a skill. Listing it here for the user's awareness, ranked LOW per the honest-rank principle.

---

## Considered and refused

- `keynote-export-fixer` — Mentioned in LOG.md 2026-03-19, but only once and the workaround is now documented. Single occurrence; not a skill.
- `humanize-draft` — Already installed system-wide as `humanizer`. Skipped to avoid duplicate proposal.
- `firecrawl-research-batch` — LESSONS_LEARNED.md #5 references it, but Firecrawl is the user's existing tool (per global CLAUDE.md). The user's CLAUDE.md is the right place for the convention, not a new skill.

## What to do next

The HIGH candidates are the build queue. Scaffold `source-citation-check` first — it pairs with `humanizer` and would be the second skill to hit the "general-purpose AND likely to be used often" bar. Then `clarify-intent`, using the upstream as the starting point. The MEDIUM candidates can sit as templates in `~/Documents/Claude/MBA-templates/`. The LOW candidate stays here as a tripwire — if it shows up in the next case retrospective, promote.
