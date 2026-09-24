# Agentic Knowledge Work Method
*A folder pattern, four artifacts, and a learning loop for working with AI agents on real, accountable knowledge work.*

**Version 0.2.0**. See [CHANGELOG.md](CHANGELOG.md).

If you've used Claude or ChatGPT for serious work and noticed your second project doesn't go meaningfully faster than your first — that's not the model. It's the missing scaffolding around the model. This repo gives you that scaffolding.

**Read the longer write-up:** [How I Work With AI Agents — and Why the Method Compounds](https://lulstrup.medium.com/how-i-work-with-ai-agents-and-why-the-method-compounds-360c75ed0f76)

## What's in here

```
templates/      drop-in starter files for any new project (LOG, LESSONS_LEARNED, RUBRIC, Research/, README)
skills/         seven core Claude Skills plus two optional git skills
examples/       sample output from mine-skills-from-project on an MBA case project
guides/         five short how-to docs covering the trickiest parts
METHOD.md       full method documentation
```

## Quick start (5 minutes)

1. Copy the contents of `templates/` into a new project folder.
2. Open `README.md` and write three lines: who this project is for, what done looks like, and the deadline.
3. Ask your agent to read the project folder and ask you clarifying questions until you both understand the intent.
4. Run the loop (curate research → build rubric → iterate work → log/reflect → mine skills).
5. At project end, run the `mine-skills-from-project` skill. The output proposes new Claude Skills to add to either the project's `.claude/skills/` or your system-wide skills library.

By project five, your skill library is rich enough that the system around the agent — not the agent itself — is the differentiator.

> **Highly recommended (optional): track your project with [git](https://git-scm.com/).** Each iteration becomes a checkpoint you can revert to if a revision goes wrong. The agent runs every git command for you — you don't need to learn the command line first. New to git? Read **[guides/05-git-and-version-control.md](guides/05-git-and-version-control.md)** — it's a friendly explainer aimed at non-technical knowledge workers. The method works without it; the method is significantly better with it.

## The method in one paragraph

Treat the agent the way a senior professional treats a high-potential apprentice. Give it clear intent, curated reference material, a quality standard, and a working memory. Capture lessons during the project, not after. At the end, mine those lessons for reusable skills that survive into the next project. The output gets better and faster as the system you've built around the agent compounds.

## The five-file folder pattern

Every project, regardless of size or domain:

```
PROJECT/
├── README.md              what this project is, who it's for, what done looks like
├── LOG.md                 timestamped action log — even meandering steps
├── LESSONS_LEARNED.md     deeper reflection, captured as it happens
├── RUBRIC.md              the quality gate the agent uses for self-evaluation
├── Research/              curated source material, with an index
│   └── README.md
├── work products/         the actual deliverables (slides, docs, code, etc.)
└── .claude/skills/        project-local skills that emerge during the work
```

## The four-stage loop

```
   1. Clarify intent  →  2. Curate research  →  3. Build rubric
                                                        │
                                                        ▼
       ┌─────────────────────────  4. Iterate work, log, reflect
       │
       │   (loop until rubric passes)
       │
       ▼
       5. Skills mining
```

Stages 1-3 typically take 60-90 minutes upfront. Stage 4 is the bulk of the project — iterations are *assumed*, not exceptional. Stage 5 is short and is what makes the method compound.

## Skills included

| Skill | What it does |
|---|---|
| `init-knowledge-work-project` | Scaffold a new project folder with the five-file pattern |
| `clarify-intent` | Q&A loop that locks success criteria before any work starts |
| `curate-research-folder` | Build an annotated `Research/` folder from a topic + a few seed sources |
| `build-project-rubric` | Generate a project-specific QA/QC rubric (big-picture + tactical) |
| `log-step` | Append a timestamped entry to `LOG.md` |
| `reflect-lesson` | Append a structured entry to `LESSONS_LEARNED.md` |
| `mine-skills-from-project` | At project end, read LOG + LESSONS and propose new reusable skills |
| `init-git-repo` *(optional)* | Initialize git tracking on the project folder with a sensible `.gitignore` |
| `commit-iteration` *(optional)* | Commit a checkpoint with a useful message after each meaningful iteration round |

Each skill is a single `SKILL.md` file with a description, trigger phrases, and a working prompt. Drop the folder into your `~/.claude/skills/` (system-wide) or `PROJECT/.claude/skills/` (project-local).

## Guides

- [Getting started](guides/01-getting-started.md) — first project, step by step
- [Writing rubrics that catch issues](guides/02-writing-good-rubrics.md) — the rubric is the quality gate; this is how to make one that works
- [Research folder discipline](guides/03-research-folder-discipline.md) — curated, not exhaustive
- [When to promote a skill](guides/04-when-to-promote-a-skill.md) — project-local vs system-wide
- [Git and version control for non-technical knowledge workers](guides/05-git-and-version-control.md) — friendly intro for anyone who's never used git; the agent runs every command for you

## License

MIT. Use it, fork it, ship it. If you build skills you'd like to share back, PRs welcome.

## Author

Built and maintained by [Leif Ulstrup](https://www.linkedin.com/in/leifulstrup) — founder of [Primehook Technology](https://www.primehookllc.com), MBA faculty at the [Kogod School of Business](https://kogod.american.edu) at American University.

This repo is a working artifact, not a product. The method evolves as I run more projects with it. Issues and PRs welcome.
