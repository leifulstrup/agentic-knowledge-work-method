---
name: mine-skills-from-project
description: Reads a finished (or near-finished) project's log, lessons, and work products to propose new reusable Claude Skills that would have made the work faster, more consistent, or higher quality. Outputs a ranked, build-ready list with each candidate's draft SKILL.md plus a placement recommendation (project-local vs system-wide). This is the compounding step in the agentic knowledge-work method — once per project, payoff across every project after. Use when the user says "mine skills", "skills retrospective", "what skills did we discover", "end-of-project review", "what should I build next", or asks for a project retrospective focused on tooling and reuse.
when_to_use: Trigger phrases include "mine skills", "mine skills from this project", "skills retrospective", "what skills did we discover", "end-of-project review", "what should I build next", "what reusable patterns emerged", "post-mortem the tooling", "what skills would have helped here". Also relevant after a deliverable has shipped and the user wants to harvest reusable patterns before context fades.
allowed-tools: Read Glob Grep Write Bash(date *) Bash(ls *) Bash(find *) Bash(mkdir *) Bash(wc *)
---

# mine-skills-from-project

Read a finished project and propose reusable Claude Skills that would have made it faster, more consistent, or higher quality. The output is a ranked proposal document the user can build from on their own schedule — not auto-installed skills.

This skill is **the compounding step** in the agentic knowledge-work method. Other skills run inside a single project. This one runs once at project end and produces leverage that pays back across every project after.

## Workflow

1. **Readiness check.** Confirm the project is finished or close to finished. If active work is still in progress, lessons haven't settled — say so and offer to defer. Skill is premature unless one of: (a) the deliverable has shipped, (b) the user explicitly says "I want a retrospective now", (c) the project is being abandoned and the user wants to harvest before closing it.

2. **Survey the project surface.** Before reading anything in depth, list what's actually here:
   - `LOG.md` (or `log.md`, `WORKLOG.md`, `journal.md`) — the running log of tactical moves
   - `LESSONS_LEARNED.md` (or `LESSONS.md`, `lessons-learned.md`, `retro.md`) — explicit lesson capture
   - `README.md` — the intent and success criteria
   - `RUBRIC.md` — QA dimensions, if the project followed the method
   - `Research/` — curated source material
   - The deliverable artifacts themselves (decks, memos, code, drafts)
   - Existing `.claude/skills/` in the project — to avoid duplicate proposals
   - Existing `~/.claude/skills/` (the user's system-wide installed skills) — to avoid proposing things already installed system-wide
   - Any project-specific run logs (e.g., `humanizer-runs/`, `reviews/`, `iterations/`) — recurring runs are themselves a recurrence signal

   Use `ls`, `find`, `Glob`. Don't `cat` everything yet — survey first, read deliberately.

3. **Refuse to mine an empty project.** If the survey turns up no LOG, no LESSONS, no work products, and no run logs — there is nothing to mine. Say so. Propose zero skills. Suggest the user run the project through the method's `log-step` and `reflect-lesson` skills next time so there's signal to mine later. Do not fabricate candidate skills from a README alone.

4. **Read deliberately.** With the survey in hand, read the files that carry signal:
   - `LOG.md` end to end — look for patterns that repeated (visual review iterations, citation checks, render-then-fix cycles), wrong turns that cost time, manual steps the agent or user did multiple times.
   - `LESSONS_LEARNED.md` end to end — each entry is a candidate signal. Lessons that explicitly flag "skill opportunity" or "this should be automated" or "next time, …" are the strongest candidates.
   - `README.md` — for project intent (what kind of work was this, what audience, what deliverable). Use this to judge whether a candidate skill is project-specific or generalizable.
   - The deliverable artifacts — to see which artifact-creation patterns recurred (e.g., "three two-column comparison slides" → a slide-template skill).
   - Run logs (`humanizer-runs/` and similar) — the *existence* of an accumulating run log is itself a signal that the underlying skill is working; the *contents* may reveal sub-patterns worth their own skill.

5. **Cluster the candidates.** Often three to five lessons point to the same underlying skill. Group them. A single underlying skill backed by five log entries is stronger than five separate one-off skills.

6. **Apply the recurrence filter.** Drop candidates that don't pass:
   - **Happened once → log entry, not a skill.** The signal is recurrence, not novelty.
   - **Domain-specific to this project → not a skill, or project-local only.** A pattern that only applies to this client, this case, this codebase doesn't merit a system-wide skill. It may merit a project-local skill or a CLAUDE.md note.
   - **Already installed system-wide → not a candidate.** Read `~/.claude/skills/` first. If the user already has `humanizer`, don't propose another humanize-text skill.
   - **Already in the backlog → reference the backlog entry, don't re-propose.** If a user maintains a candidate-skills backlog (common in the method), check it.

7. **For each surviving candidate, draft a build-ready spec.** Each spec includes:
   - `name` in `kebab-case`
   - One-paragraph `description` (third person, leads with action verb, ≤ 500 chars)
   - `when_to_use` trigger phrases (the words the user would actually type)
   - `allowed-tools` — the minimum set
   - A draft SKILL.md body with workflow steps and an output format
   - Lesson sources (which LOG or LESSONS entries motivate this candidate)
   - Recurrence count (how many times the pattern showed up)

8. **Rank HIGH / MEDIUM / LOW.** Two factors:
   - **Frequency** the pattern would recur in *similar future projects* (not just this one)
   - **Cost saved per occurrence** (qualitative — "saves ~3 hours of manual review", not "saves 73 minutes")

   HIGH = both factors strong. MEDIUM = one strong, one moderate. LOW = both moderate, or one weak. If a candidate is honestly LOW, label it LOW. The ranking is for the user's planning, not for flattery.

   **What a good ranking justification looks like:**

   - ✓ *"HIGH · 3 occurrences across this project, would recur on every consulting memo (~6 per quarter). Saves ~30 min per occurrence on the most-skipped pre-publish check. Pairs with `humanizer` which catches the related fabrication failure mode."*
   - ✗ *"HIGH · This would be really useful and would save a lot of time. Definitely worth building."* (no recurrence count, no frequency model, no cost grounding)
   - ✗ *"HIGH · I see this pattern a lot."* (vibes; not auditable)

   **Honest distributions, not padded ones.** If the project surfaced one honest HIGH and four LOW, that is the right answer. Do not promote LOWs to MEDIUM to make the list look productive. The user trusts the ranking; padding burns that trust.

9. **Recommend placement.**
   - **System-wide** (`~/.claude/skills/`) — applies to most projects the user does, general-purpose, high-frequency. The user's stated bar: "general-purpose AND likely to be used often." Conservative default; humanizer is the reference example.
   - **Project-local** (`.claude/skills/` in this project, or in a sibling project of the same type) — applies to a specific domain, client, or codebase.
   - **CLAUDE.md note, not a skill** — applies but the cost of building a skill exceeds the cost of writing a one-paragraph note in CLAUDE.md.
   - **Templates snippet, not a skill** — a recurring artifact (slide layout, memo header, rubric structure) that doesn't need agentic logic. Better as a copyable template.

   When in doubt, default to project-local. The user's stated rule: promote to system-wide after using it across two to three projects with success.

10. **Write the output file.** Save to `<project-root>/skills-mined-<YYYY-MM-DD>.md`. Use today's date — fetch with `!`date +%Y-%m-%d`` if available, or via `Bash(date +%Y-%m-%d)`. The dated filename preserves history if the skill runs more than once on the same project. Use the format in the next section.

11. **Report.** Output a short summary to the user. The substance lives in the file — the chat report exists only to tell the user the file is there and surface the headline. Exact shape:

    ```
    Mined <project-name>: <H> HIGH, <M> MEDIUM, <L> LOW (<R> refused, <I> already installed).
    Top candidate: <name> (<placement>).
    Saved to: <path-to-skills-mined-YYYY-MM-DD.md>.
    Next: review the HIGH candidates and decide which to scaffold first.
    ```

    No preamble. No narration of the steps just taken ("I surveyed the project...", "I read LOG.md..."). The four lines above are the entire chat response.

    Do not auto-implement any skill. Propose only.

Full worked example: see [examples/sample-skills-mined.md](../../examples/sample-skills-mined.md).

## Output format

```markdown
# Skills mined from <project-name>

*Generated <YYYY-MM-DD>. Surveyed: LOG.md (<N> entries), LESSONS_LEARNED.md (<M> lessons), <other artifacts>. Existing skills checked: system-wide (<count>), project-local (<count>).*

## Summary

- HIGH priority: <count>
- MEDIUM priority: <count>
- LOW priority: <count>
- Refused (single-occurrence or domain-specific): <count>
- Already installed (skipped): <count>

## Build first — HIGH priority

### #1 (HIGH · system-wide) · `<skill-name>`

**Lesson sources.** <link or quote the LOG/LESSONS entries that motivate this>

**Recurrence count.** <N times across the project>

**ROI estimate.** <qualitative — "would have saved ~3 hours across 4 iterations">

**Placement.** System-wide because <reason>.

**Draft SKILL.md.**

```yaml
---
name: <skill-name>
description: <one paragraph>
when_to_use: <trigger phrases>
allowed-tools: <minimum set>
---
```

<workflow steps>
<output format>

---

### #2 (HIGH · project-local) · `<skill-name>`

<repeat>

## Build next 2–3 projects — MEDIUM priority

### #N (MEDIUM · ...) · `<skill-name>`

<same shape, abbreviated>

## Backlog — LOW priority

### #M (LOW · ...) · `<skill-name>`

<abbreviated; one paragraph plus lesson sources>

## Considered and refused

- `<skill-name>` — single occurrence; logged but not proposed.
- `<skill-name>` — already installed at `~/.claude/skills/<name>`.
- `<skill-name>` — domain-specific to this project; better as a CLAUDE.md note.

## What to do next

<one to three sentences — which candidates to scaffold first and why>
```

## Operating principles

- **Recurrence is the signal.** A pattern that happened once is a log entry. A pattern that happened three times is a candidate skill.
- **Cost saved per occurrence > frequency alone.** A skill that saves 30 minutes once a year may matter more than one that saves 2 minutes every project — depending on the user's cadence and what's expensive in their work.
- **Project-local until proven broadly useful.** Default placement is project-local. Promote to system-wide after the skill has earned its keep on two to three projects.
- **The output is a proposal, not a fait accompli.** This skill never installs anything. It writes a markdown file. The user decides what to build.
- **Trust the user's existing taxonomy.** If the user has a candidate-skills backlog, cross-reference it. If they have a "promotion rule" in their notes, respect it.
- **Honest LOW labels.** Do not over-rank to seem productive. A LOW candidate labeled LOW gives the user signal; a LOW candidate labeled HIGH burns trust.

## What NOT to do

- Don't propose skills the user already has installed. Survey `~/.claude/skills/` and the project's `.claude/skills/` first.
- Don't propose skills from a single occurrence. The signal is recurrence; one occurrence is a log entry.
- Don't fabricate candidates to fill out the list. If a project has only one mineable pattern, propose one. If it has zero, propose zero and say so.
- Don't invent ROI numbers. Use qualitative language ("would have saved several hours across the project") rather than fake precision ("saves 47 minutes per run").
- Don't auto-implement. Propose only. The user builds on their own schedule.
- Don't propose skills outside the user's domain. If the project is consulting/teaching/writing, don't propose a CI/CD pipeline skill because some lesson mentioned a deploy step in passing.
- Don't over-rank. If only one candidate is honestly HIGH, the rest are MEDIUM or LOW. Don't pad.
- Don't write the user's CLAUDE.md or settings.json for them. If a proposal would be better as a CLAUDE.md note or a hook, say so and let the user write it.
- Don't bury the refusal. If the project is too sparse to mine, lead with that, not with a forced list.
- Don't run mid-project unless the user explicitly asks. Mining before lessons settle produces premature candidates that miss what actually mattered.
- Don't narrate in the chat report. The file is the deliverable. The chat is a four-line pointer to the file. No "I'll now…" preambles, no "Here's what I found…" recaps, no apology if a section was sparse.
- Don't pad the rank distribution. An honest one-HIGH, zero-MEDIUM, four-LOW project is a useful audit trail. A fabricated three-HIGH, three-MEDIUM project is noise.

## Edge cases

- **Project has LOG but no LESSONS** — proceed with LOG only. Note in the output that the lesson signal is missing and that candidates lean toward LOG-derived patterns. Recommend the user run `reflect-lesson` (or any equivalent) before the next retrospective.
- **Project has LESSONS but no LOG** — proceed with LESSONS. The lesson capture is the higher-signal source anyway; LOG is corroboration.
- **Project has neither, but has substantial work products** — work products alone can be mined for artifact-pattern skills (recurring slide layouts, recurring memo structures). Note the lower signal-to-noise.
- **Project has only a README** — refuse. There is nothing to mine. See workflow step 3.
- **Project uses a non-method folder shape** — adapt. The method's folder pattern is a convenience, not a requirement. Look for journal-like and lesson-like files regardless of name.
- **User runs the skill twice on the same project** — produce a new `skills-mined-<date>.md` rather than overwriting. The user can diff to see what changed since last run. Reference the prior file in the new one's preamble.
- **User asks to mine across multiple projects at once** — out of scope for this skill. Each project gets its own retrospective. Suggest running the skill once per project and then aggregating manually (or building a cross-project mining skill as a candidate proposal).
- **User asks to immediately scaffold the top HIGH candidate** — the skill proposes; it doesn't build. If asked, hand off to the user's skill-authoring workflow (which is itself the kind of pattern that may be a candidate skill).

## Revision notes

May 2026 revision. It keeps the original core: recurrence as the signal, HIGH/MEDIUM/LOW ranking, a placement recommendation, and build-ready output. It adds these changes:

- a `when_to_use` trigger list and tightened `allowed-tools`
- a guard that refuses to mine projects too sparse to show a pattern
- dated output filenames (`skills-mined-<date>.md`), so reruns never overwrite earlier results
- a check against skills already installed system-wide and against any candidate-skills backlog
- a longer edge-cases section
