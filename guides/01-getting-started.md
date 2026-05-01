# Getting Started — Your First Project With This Method
*A 30-minute walkthrough for the first time you use the agentic knowledge-work method.*

If you've never run this method before, this guide gets you to a working state in about 30 minutes. The method scales up after that, but the first project should be small — a deliverable you'd already need to produce this week.

## Before you start

Pick a project that meets all three:

1. **Real deliverable.** Something you'd produce anyway — a memo, a deck, a code refactor, a research summary, a one-pager.
2. **Modest scope.** 2-8 hours of work total. Not a 6-week strategic plan; not a 5-minute one-off.
3. **Has a clear audience.** A person or team who'll read or use the artifact.

Bad first projects: "explore AI capabilities," "see what Claude can do for marketing," "build me a chatbot." Those are tool exploration, not knowledge work.

Good first projects: "draft the Q3 board review memo," "outline the new-employee onboarding doc," "build the spreadsheet that compares the three vendor quotes," "review last quarter's pipeline data and find anomalies."

## Step 1 — Make the folder (5 minutes)

Pick a folder name and location. Then create the five-file scaffold:

```bash
mkdir -p ~/projects/your-project-name
cd ~/projects/your-project-name
cp -r /path/to/this/repo/templates/* .
```

You now have:

```
your-project-name/
├── README.md
├── LOG.md
├── LESSONS_LEARNED.md
├── RUBRIC.md
└── Research/
    └── README.md
```

Do not edit any of these yet. The agent will help you.

**Optional but recommended:** if this is your second or later project with the method, also ask the agent to initialize git on the folder now (run the `init-git-repo` skill). The agent does the work; you don't need to type any commands. Read [`05-git-and-version-control.md`](05-git-and-version-control.md) for the friendly introduction. If this is your first project, skip git entirely — the method works without it. Add it on project 2 once the folder pattern feels comfortable.

## Step 2 — Lock the intent with the agent (15 minutes)

Open a fresh Claude Code (or Claude Cowork, or your agent of choice) session in the project folder. Tell the agent:

> Read this folder and run the `clarify-intent` skill. I want to lock the project's intent, audience, deliverable, deadline, and constraints before we start.

The agent will walk you through the five-category interview. Answer specifically. The most common failure mode here is being too vague — "good slides" instead of "audience can recall the central claim three weeks later."

When the agent has populated `README.md`, read it back. Edit if anything's wrong. This file is the agent's ground truth for the rest of the project.

## Step 3 — Curate research (5-15 minutes)

Tell the agent:

> Run `curate-research-folder`. I want to seed it with a few sources I trust, and then have you fill in any gaps based on the project intent.

Give the agent 2-5 of your own go-to sources. The agent fills in gaps with primary-source material it can find. The folder ends up with maybe 5-12 items — small, curated, useful.

## Step 4 — Build the rubric (5-10 minutes)

Tell the agent:

> Run `build-project-rubric`. Generate a project-specific QA/QC rubric based on the README and the curated Research/.

The agent drafts a rubric with three dimensions (first-principles, tactical-quality, project-specific). Read it. Edit. The rubric is a living document; you'll add criteria as you go.

## Step 5 — Iterate the work, with logging (the bulk of the project)

Now the actual work. Ask the agent to start producing the deliverable. Tell it explicitly:

> After every meaningful step, run `log-step` to append to LOG.md. When something interesting happens — a problem fixed, a surprise, a counter-intuitive finding — run `reflect-lesson` to append to LESSONS_LEARNED.md.

Iterate. The first draft will be wrong. The second draft will be closer. By the third or fourth, it should pass the rubric.

The discipline that matters here: **iterate against the rubric, not against vibes**. If the agent says "the deck is ready," ask it to score itself against `RUBRIC.md`. Any 0 means not ready.

**If you initialized git in Step 1**, also tell the agent: *"After each iteration round that crosses a meaningful boundary, run `commit-iteration` to save a git checkpoint with a useful message."* This costs nothing during the project — and the first time a revision goes the wrong way and you want the previous version back, you'll be glad it's there.

## Step 6 — Mine for skills (5-10 minutes)

After you ship the deliverable, run:

> Run `mine-skills-from-project`. Read LOG.md and LESSONS_LEARNED.md and propose new Claude Skills that would have made this project faster or higher quality.

The output is a ranked proposal. Implement two or three of the HIGH-ranked skills before your next similar project. Watch the next project go faster.

## What success looks like after one project

- Your folder has all five files populated, plus the curated `Research/`.
- You shipped a deliverable that scored 3.5+ on the rubric.
- You have a `skills-mined.md` file with 3-10 skill proposals, ranked.
- You have `LESSONS_LEARNED.md` with 2-5 distilled lessons.

If all four are true, the method worked.

## What success looks like after five projects

- Your `~/.claude/skills/` library has 10-25 skills accumulated from past projects.
- Your fifth project takes 30-50% less time than your first did, for the same quality.
- You can hand a similar project to the agent on day one and have it produce a credible first draft within an hour because the skill library handles the boilerplate.

That's the compounding. It's real but it requires the discipline. The first project is the slowest one; every subsequent project earns interest on the system you've built.

## Common pitfalls on the first project

- **Skipping `clarify-intent` because you "know what you want."** You don't, until you've answered the five categories explicitly. Skipping this step is the #1 cause of off-track agent work.
- **Letting the rubric be generic.** A rubric that says "high quality" doesn't catch anything. Specific criteria catch specific failure modes.
- **Capturing lessons at the end instead of mid-project.** The retrospective lesson is always weaker than the in-the-moment one.
- **Implementing every skill the mining step proposes.** Don't. Pick two or three HIGH-ranked. The rest can wait until you've used the strongest ones in a real project.

## When you're ready for the second project

The second project starts with three differences:

1. You have skills installed from the first project's mining step.
2. You have a populated example of what good rubric criteria look like.
3. You know which lessons from the first project applied broadly vs. were one-off.

Carry forward the skills. Carry forward the rubric format (but rebuild the specific criteria — they're project-specific). Carry forward the lessons that were broadly applicable, by promoting them into your skills.

The method gets richer with use. The discipline is the same.
