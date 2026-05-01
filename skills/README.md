# Starter Claude Skills
*Seven skills that automate the core method.*

Each subfolder contains a single `SKILL.md` file with a description, trigger phrases, and a working prompt. To install:

```bash
# System-wide (used across every project)
cp -r skills/init-knowledge-work-project ~/.claude/skills/

# Project-local (only used in this project)
cp -r skills/init-knowledge-work-project /path/to/project/.claude/skills/
```

## When to install where

- **System-wide (`~/.claude/skills/`)** — for skills that apply across many project types. The seven starter skills below are all good system-wide candidates.
- **Project-local (`PROJECT/.claude/skills/`)** — for skills specific to a single project's domain or conventions. Slide-deck-specific skills, code-style skills tied to a particular codebase, etc.

A skill that starts project-local can be promoted to system-wide once you've used it across two or three projects and confirmed it's broadly useful. See [guides/04-when-to-promote-a-skill.md](../guides/04-when-to-promote-a-skill.md).

## Skills index

### Core skills

| Skill | What it does | When to invoke |
|---|---|---|
| [`init-knowledge-work-project`](init-knowledge-work-project/) | Scaffolds a new project folder with the five-file pattern | Day 1 of any new project |
| [`clarify-intent`](clarify-intent/) | Q&A loop that locks success criteria | After the folder is scaffolded, before any work starts |
| [`curate-research-folder`](curate-research-folder/) | Builds an annotated `Research/` folder | Once intent is locked |
| [`build-project-rubric`](build-project-rubric/) | Generates a project-specific QA/QC rubric | Once research is curated |
| [`log-step`](log-step/) | Appends a timestamped entry to `LOG.md` | After every meaningful action |
| [`reflect-lesson`](reflect-lesson/) | Appends a structured entry to `LESSONS_LEARNED.md` | When something interesting happens — surprise, failure mode, insight |
| [`mine-skills-from-project`](mine-skills-from-project/) | Reads LOG + LESSONS and proposes new reusable skills | At project end |

### Version-control companions (optional, highly recommended)

These skills add git checkpoint discipline to the iteration loop. The user does not need to know git — these skills run every command. See [`../guides/05-git-and-version-control.md`](../guides/05-git-and-version-control.md) for the friendly intro.

| Skill | What it does | When to invoke |
|---|---|---|
| [`init-git-repo`](init-git-repo/) | Initializes git on the project folder with a sensible `.gitignore` and an initial commit | Optional, recommended after `init-knowledge-work-project` |
| [`commit-iteration`](commit-iteration/) | Commits a checkpoint with a useful, audit-trail-quality message after each iteration round | After each meaningful iteration boundary (rubric score lift, gap closed, structural revision) |

The seven core skills compose. The output of one becomes the input to the next. The two version-control skills are optional companions — adding them increases reversibility and produces a permanent audit trail of how a project evolved.
