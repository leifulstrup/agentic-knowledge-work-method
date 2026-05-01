# The Agentic Knowledge Work Method
*A folder pattern, four artifacts, and a learning loop for working with AI agents on real, accountable knowledge work.*

This document is the long-form companion to the [Medium piece](#) and the [README](README.md). The Medium piece is the friendly introduction. This document is the operational reference.

## The premise

Treat AI agents the way a senior professional treats a high-potential apprentice. Give them clear intent, curated reference material, a quality standard you can both check, a working memory of what's been tried, and a way to capture lessons that survive the project.

Do that, and the agent gets better at *your* work over time — not just at AI generally.

## The artifacts

The method requires five files in one folder pattern. Every project, regardless of size or domain.

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

Each file has one job:

| File | Job |
|---|---|
| `README.md` | What is this project? What does done look like? |
| `LOG.md` | What did we do, in what order, with what result? |
| `LESSONS_LEARNED.md` | What did we *learn* — distilled, durable, transferable? |
| `RUBRIC.md` | How do we know the work is good? |
| `Research/` | What sources do we trust as ground truth? |

The folder is the agent's working memory. The agent reads it at the start of every session.

### Optional but highly recommended: track the folder with git

Once the folder pattern is in place, the strongest single addition is to put it under [git](https://git-scm.com/) version control. Each iteration becomes a checkpoint. A revision can be inspected, compared against earlier states, or reverted entirely. Months later, you can read the iteration history and reconstruct exactly how the project evolved.

The agent runs every git command for you (`git init`, `git add .`, `git commit -m "..."`, `git log`, `git diff`, `git checkout`). You don't need to learn the command line first. If you'd rather click than type, use [GitHub Desktop](https://desktop.github.com); the agent and Desktop coexist fine.

Why "optional"? Because the method works without it. A first-timer can run the method end-to-end on a project without git and still get the compounding benefit. **Why "highly recommended"?** Because once you've used git on one project, the third-iteration moment when a revision goes the wrong way and you can simply `git checkout` back to Iteration 4 changes how you feel about the entire workflow. New users: skip git on project 1. Add it on project 2. Read [`guides/05-git-and-version-control.md`](guides/05-git-and-version-control.md) — a friendly explainer aimed specifically at non-technical knowledge workers.

## The loop

```
   1. Clarify intent  →  2. Curate research  →  3. Build rubric
                                                         │
                                                         ▼
       ┌───────────────────────────  4. Iterate work, log, reflect
       │
       │   (loop until rubric passes)
       │
       ▼
       5. Skills mining
```

Five stages. The first three are setup. The fourth is the bulk of the work — iteration is *assumed*, not exceptional. The fifth is short and is what makes the method compound.

### Stage 1 — Clarify intent

Before any work begins, lock five categories:

1. **Intent** — what are we trying to accomplish, in one sentence?
2. **Audience** — who is this for, named?
3. **Deliverable** — what artifact, in what format, where does it live?
4. **Deadline** — when, and what's the bar for "done enough"?
5. **Constraints** — what should the agent know upfront?

The agent runs the `clarify-intent` skill. The output is a populated `README.md`. This step takes 15-30 minutes for a typical project. Skipping it is the #1 cause of wasted agent work.

### Stage 2 — Curate research

The agent runs `curate-research-folder`. This combines:

- Your own seed sources (2-5 things you already trust)
- Agent-found primary sources (papers, primary documents, named-publication articles)
- Domain best-practice references

The folder ends up with 5-15 items, each with a one-line note in the index. Quote-aggregator sites are excluded; primary sources only.

### Stage 3 — Build rubric

The agent runs `build-project-rubric`. The rubric has three dimensions:

- **First-principles** (does the work answer the question?) — 30-40% weight
- **Tactical-quality** (are the artifacts well-made?) — 30-40% weight
- **Project-specific** (failure modes unique to this project) — 20-40% weight

The third dimension starts small and grows during the project as failure modes are discovered. The rubric is a living document.

### Stage 4 — Iterate, log, reflect

The agent produces the deliverable, iteratively. After every meaningful step, the agent runs `log-step` to append to `LOG.md`. When something interesting happens — a failure mode caught, a counter-intuitive insight, a workflow surprise — the agent runs `reflect-lesson` to append to `LESSONS_LEARNED.md`.

Iteration is assumed. A typical knowledge-work project runs 5-30 revision rounds before the rubric passes. Each round produces concrete artifacts (a new draft, a new render, a new test result). The rubric is checked after every substantive change.

### Stage 5 — Mine skills

At project end, the agent runs `mine-skills-from-project`. The skill reads `LOG.md` and `LESSONS_LEARNED.md` and outputs a ranked list of new candidate Claude Skills with full draft `SKILL.md` bodies. Each candidate is recommended for project-local or system-wide placement.

You implement two or three of the HIGH-priority candidates before your next similar project. The skills library grows. The system around the agent compounds.

## Why this method works

Three structural reasons:

### 1. The folder is the agent's working memory

Most agent failures come from missing context. The agent doesn't remember the last session. It doesn't know which sources you trust. It doesn't know what "done" looks like. The folder solves all three.

When the agent starts a new session, it reads `README.md` (intent), `LOG.md` (what's been tried), `LESSONS_LEARNED.md` (what's been learned), `RUBRIC.md` (the quality bar), and `Research/` (ground truth). The agent inherits the project's full context in 30 seconds.

### 2. The rubric forces self-evaluation

The agent will declare work "done" when asked. Without a rubric, "done" means "the agent stopped." With a rubric, "done" means "the rubric passes."

The rubric is structured so the agent can apply it without ambiguity. Each criterion has a specific exemplary description. Each is scored 0-4. Disqualifying scores are explicit. The agent can self-evaluate, surface gaps, and propose specific revisions.

### 3. The mining step makes the method compound

Without a mining step, every project is a one-off. The lessons get filed in a doc nobody reads again. The skills that should have emerged stay in the user's head.

With a mining step, every project ends by surfacing the patterns that recurred and the insights that had operational implications. Some become reusable skills. The skills accumulate. The system gets better.

This is the part most "how to use AI" content misses entirely. The agent isn't the asset — the system you build around the agent is. The mining step is what makes the system grow.

## What this method does NOT do

- **It does not replace skill, taste, or judgment.** The agent's output still needs your eye. The method makes that eye more efficient, not optional.
- **It does not work with vague projects.** If you can't articulate the intent in one sentence, the method has nothing to do until you can.
- **It does not eliminate iteration.** The fourth stage is where most of the time goes. The method makes iteration *productive*, not faster per round.
- **It does not work on projects you don't care about.** The discipline costs ~30 minutes of upfront setup. If the project doesn't merit that investment, just chat with the agent and move on.

## How long does it take?

Setup: 30-90 minutes for stages 1-3, depending on project size.

Iteration: variable — anywhere from 2 hours to 2 weeks, depending on the project. The method doesn't make iteration faster *per round*; it makes each round productive instead of wasted.

Mining: 15-30 minutes at the end.

Total overhead vs. no method: roughly 1-2 hours per project. Total saved by the compounding skills library: dozens of hours per year, growing as the library grows.

## The compounding claim, made specific

By project five, expect:

- Your `~/.claude/skills/` library has 10-25 skills accumulated from past mining steps
- Your fifth project takes 30-50% less time than your first did, for the same quality
- You can hand a similar project to the agent on day one and have it produce a credible first draft within an hour because the skill library handles the boilerplate

By project twenty:

- Your skill library has 50-100 skills, organized by domain
- New projects in familiar domains produce a credible first draft *during the kickoff conversation*
- Your role shifts from "doing the work" to "directing the agent" for routine work, freeing you for the parts that actually require human judgment

This is not a forecast — it's what the method has produced in projects to date. The compounding is real. The discipline is the cost. The output quality and the recovered time are the return.

## When to use this method

Use it when:

- You have a deliverable that matters
- You'll iterate (any non-trivial project will)
- You want the work to compound — you'll do similar projects in the future
- You're tired of agent results being inconsistent

Don't use it when:

- You're exploring tool capabilities, not producing a deliverable
- You're doing a one-off task that won't recur
- The project is genuinely too small to merit the setup cost

The method scales down to a 30-minute task and up to a 30-day project. The discipline is the same. The compounding is the same.

## Author and license

Written and maintained by [Leif Ulstrup](https://www.linkedin.com/in/leifulstrup) — founder of [Primehook Technology](https://www.primehookllc.com), MBA faculty at the [Kogod School of Business](https://kogod.american.edu) at American University.

This document is licensed under MIT (see [LICENSE](LICENSE)). The method itself is given freely. If you use it and learn things, the most useful thing you can do is open a PR with your additions or share what you learned.
