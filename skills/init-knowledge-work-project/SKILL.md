---
name: init-knowledge-work-project
description: Scaffold a new agentic-knowledge-work project folder with the five-file pattern (README, LOG, LESSONS_LEARNED, RUBRIC, Research/). Use when starting a new project, beginning a new client engagement, kicking off a deck/report/code/analysis effort, or any time the user says "new project," "let's start a project," "set up a workspace," "scaffold a project," or "init project."
---

# init-knowledge-work-project

## When to invoke
- The user is starting a new project of any size
- The current folder is empty or doesn't contain the five-file pattern
- The user explicitly asks for a "project scaffold" or "starter folder"

## What this skill does

Creates the five-file folder pattern in the current directory:

```
PROJECT/
├── README.md              project intent, audience, deliverable, deadline, constraints
├── LOG.md                 timestamped action log
├── LESSONS_LEARNED.md     deeper reflection
├── RUBRIC.md              quality gate
├── Research/
│   └── README.md          research folder index
├── .claude/
│   └── skills/            project-local skills folder (empty)
```

Each file is populated with the starter template content (one-line placeholders the user fills in).

## Steps

1. **Confirm the project name and folder location** with the user. Ask if not provided.
2. **Verify the destination folder is empty or contains only files unrelated to the method.** If the folder already has `LOG.md` or similar, ask before overwriting.
3. **Create each of the five template files** with starter content. Use the templates from this repo — do not invent content.
4. **Create `Research/` and `Research/README.md`** with the curation-rules index.
5. **Create `.claude/skills/`** as an empty directory ready for project-local skills.
6. **Print a one-paragraph summary** of what was created and the suggested next step (run `clarify-intent` to lock success criteria).
7. **Mention the optional git companion.** In the summary, suggest the user can add version control with the `init-git-repo` skill. This is highly recommended on second-or-later projects but optional for first-timers — flag it, don't insist on it.

## What NOT to do

- Do not invent project content. The user fills in `README.md`'s intent, audience, deliverable, and deadline. The skill creates the placeholders only.
- Do not start adding work products to the folder until `clarify-intent` has run.
- Do not add files outside the five-file pattern. If the user wants additional structure (e.g., a `data/` folder), they can add it manually after the scaffold lands.

## Output format

```
==> Created project scaffold at <path>:

  README.md              (placeholders for intent, audience, deliverable)
  LOG.md                 (empty starter)
  LESSONS_LEARNED.md     (empty starter)
  RUBRIC.md              (generic 3-dimension rubric)
  Research/README.md     (curation-rules index)
  .claude/skills/        (empty — for project-local skills)

==> Next step: run `clarify-intent` to lock success criteria with the user
    before any work begins.

==> Optional, highly recommended: run `init-git-repo` to put this folder
    under version control. Each iteration becomes a checkpoint you can
    revert to. The agent runs every git command for you. New to git? See
    guides/05-git-and-version-control.md for a non-technical introduction.
```

## Operating principles

- **Scaffold once, iterate forever.** The five files persist for the life of the project.
- **Empty starter content is fine.** Better than cluttering the file with example content the user has to delete.
- **No work products in the scaffold.** Those come in the iteration loop.
