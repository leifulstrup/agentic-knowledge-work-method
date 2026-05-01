---
name: reflect-lesson
description: Append a structured entry to LESSONS_LEARNED.md when something interesting happens during the project. Captures what happened, why it matters, and what to do differently — distilled while the surprise is fresh, not at the end of the project. Use whenever a problem surfaces and gets solved, when a counter-intuitive finding emerges, or when a piece of the workflow worked unexpectedly well or badly. Trigger phrases include "lesson learned," "capture this," "reflect on this," "this is interesting," "we should remember this."
---

# reflect-lesson

## When to invoke
- A failure mode just got caught and fixed
- A counter-intuitive insight just emerged from the work
- A workflow step worked surprisingly well or surprisingly badly
- The user says "huh, interesting" or any equivalent
- A pattern is noticed across two or more sessions

## When NOT to invoke
- For purely tactical events (those go in `LOG.md`)
- For things that aren't actually new or surprising
- For lessons that have already been captured

## What this skill does

Appends a structured entry to `LESSONS_LEARNED.md`. Each entry is two or three short paragraphs — not a tweet, not a long essay. Format:

```markdown
---

## Lesson N · *(short title)*

**What happened.** *(the specific event that produced the insight, in 2-4 sentences)*

**Why it matters.** *(the durable principle the event reveals, in 2-4 sentences)*

**What to do differently.** *(the operational change for the next session or project, in 1-3 sentences)*

**Cross-references.** *(file names, log entries, related lessons)*

**Skill opportunity.** *(if this lesson points to a reusable Claude Skill, name it briefly)*
```

## Steps

1. **Read the current `LESSONS_LEARNED.md`** to determine the next lesson number.
2. **Capture the lesson while it's fresh.** Don't wait until end of session. Mid-event lessons are richer than retrospective ones.
3. **Distill, don't transcribe.** A lesson is not a re-telling of the event; it's the principle the event reveals.
4. **Be specific about cross-references.** Name files. Reference specific log entries. Connect to other lessons.
5. **Flag skill opportunities.** If the lesson suggests a reusable skill, name it briefly. The full skill proposal happens at project end via `mine-skills-from-project`.
6. **Append the entry** to `LESSONS_LEARNED.md`.
7. **Print a one-line confirmation.**

## What makes a good lesson

A good lesson:

- **Names a specific event** — not a category of events
- **Distills a durable principle** — one that applies beyond this project
- **Proposes a concrete change** — not "be more careful" but "always render after every change"
- **Cross-references** — connects to logs, files, or other lessons

A bad lesson:

- Is too vague to act on ("communication is important")
- Is just a re-telling of an event without distillation
- Has no operational implication

## What NOT to do

- Do not log tactical events here — they go in `LOG.md`
- Do not write essays — 2-3 short paragraphs per entry
- Do not pad with every minor surprise — the file's value is in being a curated, reflective document
- Do not assume the user agrees with the distilled principle. Run it past the user before appending if uncertain.

## Output format

After appending:

```
==> LESSONS_LEARNED.md updated. Lesson N: <short title>.

  Skill opportunity flagged: <skill name or "(none)">
```

## Operating principles

- **Mid-event capture beats retrospective capture.** Insight has a half-life; capture it before it flattens.
- **Distillation, not transcription.** The lesson is the principle, not the story.
- **Cross-reference religiously.** A lesson that doesn't connect to other artifacts is hard to use later.
