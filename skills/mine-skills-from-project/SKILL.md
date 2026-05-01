---
name: mine-skills-from-project
description: At project end, read LOG.md and LESSONS_LEARNED.md and propose new reusable Claude Skills that would have made this project faster, more consistent, or higher quality. Outputs a ranked list with build-ready skill specs and a recommendation on whether each goes project-local or system-wide. This is the step that makes the agentic knowledge-work method compound. Use only at project end. Trigger phrases include "mine skills," "what skills did we discover," "skills retrospective," "end-of-project review."
---

# mine-skills-from-project

## When to invoke
- At project end, after the deliverable has shipped
- Whenever the user runs an explicit retrospective
- NOT during active project work — the lessons need time to settle into LESSONS_LEARNED.md first

## What this skill does

Performs the end-of-project skill-mining step that makes the method compound. Reads:

- `LOG.md` — to see what tactical patterns repeated
- `LESSONS_LEARNED.md` — to see which insights had operational implications
- The work products themselves — to see which patterns of artifact-creation could be automated
- The existing `.claude/skills/` (if any) — to avoid proposing duplicates

Outputs a ranked list of new candidate skills, each with:

- A name (`kebab-case`)
- A description (what it does, when to invoke)
- A trigger-phrase list
- A first-pass `SKILL.md` body
- A recommendation on placement: project-local (`.claude/skills/`) vs system-wide (`~/.claude/skills/`)
- A priority ranking (HIGH / MEDIUM / LOW based on ROI for similar future projects)

## Steps

1. **Confirm the project is finished or close to finished.** If not, this skill is premature.
2. **Read `LOG.md`** end to end. Look for:
   - Patterns that repeated (visual review, citation checks, render iterations)
   - Wrong turns that took time
   - Manual steps the agent or user did multiple times
3. **Read `LESSONS_LEARNED.md`**. Each lesson is a candidate signal. Many lessons explicitly flag "skill opportunity" — those are the strongest candidates.
4. **Read the work products** to see which artifact patterns recurred (e.g., "we built three two-column comparison slides — that's a reusable template").
5. **Cluster** the candidates. Often 3-5 lessons point to the same underlying skill.
6. **Filter** for genuinely reusable. A pattern that only applies to *this* project domain doesn't merit a skill — that's just a `LOG.md` entry. A pattern that would apply to *any future similar project* does.
7. **For each surviving candidate, draft a `SKILL.md` body** following the standard format.
8. **Rank** the candidates HIGH / MEDIUM / LOW based on (a) frequency the pattern would recur in similar future projects and (b) cost saved per occurrence.
9. **Recommend placement.** Project-local for skills tied to a specific domain or codebase. System-wide for skills that apply broadly.
10. **Output** the ranked list in a `skills-mined.md` file in the project root, with each candidate's full draft `SKILL.md`.

## Output format

```markdown
# Skills Mined from <project-name>
*Generated <date>. Reading LOG.md (<N> entries) and LESSONS_LEARNED.md (<M> lessons).*

## Recommended for immediate build

### #1 (HIGH) · `<skill-name>` — system-wide

**Lesson source.** *(reference the lessons that motivate this)*

**ROI estimate.** *(why this skill repays its build cost)*

**Draft SKILL.md.** *(full body)*

---

### #2 (HIGH) · `<skill-name>` — project-local

*(repeat)*

## Recommended for next 2-3 projects

### #N (MEDIUM) · `<skill-name>`

*(repeat)*

## Backlog (build only if pattern recurs)

### #M (LOW) · `<skill-name>`

*(repeat)*
```

## What NOT to do

- Do not propose generic skills the user already has. Read the existing `.claude/skills/` directories first.
- Do not propose skills that only apply to a single past event. The signal is *recurrence* — patterns that repeated, lessons that pointed to the same underlying capability.
- Do not over-rank. If a candidate is honestly LOW priority, label it LOW. The user trusts the ranking.
- Do not invent ROI numbers. Use qualitative descriptions ("would have saved ~3 hours of manual review across 4 iterations") rather than fake precision.
- Do not implement the skills automatically. Output the proposals; let the user implement on their schedule.

## Operating principles

- **Recurrence is the signal.** A pattern that happened once is a log entry. A pattern that happened three times is a skill.
- **Cost-saved per occurrence matters more than frequency alone.** A skill that saves 30 minutes once a year may matter more than one that saves 2 minutes every project — depending on the user's cadence.
- **Project-local until proven broadly useful.** Default to project-local placement; promote to system-wide after the skill has been used across 2-3 projects with success.
- **The output is a proposal, not a fait accompli.** The user implements which skills get built.
