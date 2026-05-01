# Git and Version Control — for Non-Technical Knowledge Workers
*A short, friendly guide to using git on your project folders. You don't need to learn the command line. The agent runs the commands.*

If you're a developer, skip this guide — you already know everything below. If you're a knowledge worker who has never used git and the word "command line" makes you uneasy, this guide is for you.

## Why this is worth your time

The agentic-knowledge-work method involves iterating — sometimes 5, 10, 30 times — on a deliverable. Each iteration changes files. Some of those changes work. Some don't. Some you wish you could undo. Some you wish you could compare against an earlier version.

**Git is the tool that solves all four of those problems at once.** Every meaningful iteration becomes a *checkpoint*. You can return to any earlier checkpoint at any time. You can compare two checkpoints side by side. You can branch off and try an experimental direction without endangering the main version.

If your method involves iteration — and the agentic-knowledge-work method *requires* iteration — then version control is a natural fit. The article you read earlier called it "highly recommended." That's because once you've used it for one project, you'll wonder how you worked without it.

## The minimum viable knowledge

You need to understand four operations conceptually. You do *not* need to type them yourself. The agent will run them for you.

| Operation | What it does | When to run |
|---|---|---|
| `git init` | Tells git to start tracking this folder | Once, at project start |
| `git add .` | Marks all current changes for the next checkpoint | Before any commit |
| `git commit -m "message"` | Saves a checkpoint with a short message describing what changed | After any meaningful iteration |
| `git log` | Shows the history of checkpoints | Whenever you want to review where you've been |

Two more operations you'll occasionally want:

| Operation | What it does | When to run |
|---|---|---|
| `git diff <commit>` | Shows what changed since a previous checkpoint | When you want to see what got edited between iterations |
| `git checkout <commit>` | Returns the folder to an earlier checkpoint | When a revision went the wrong way and you want to back up |

That's it. Six operations. Two of them are emergencies-only.

## The agent runs all of this for you

The genuinely friendly part: **you don't have to type any of these commands.** Tell the agent something like:

> "Set up git tracking on this project folder, and commit a checkpoint after every iteration we complete."

The agent runs `git init`. It runs `git add .` and `git commit -m "..."` after each meaningful step. It writes useful commit messages — `"Iteration 3: rubric score 3.4 → 3.7, fixed accessibility gap"` — that read as a useful audit trail months later.

When you want to see history, ask:

> "Show me the git log."

When you want to compare two iterations, ask:

> "What changed between Iteration 4 and Iteration 5?"

When you want to back up to an earlier state:

> "Revert this folder to Iteration 4."

The agent translates each request into the right git command and runs it.

## If you'd rather use a graphical app

Don't want any command-line at all? Install [GitHub Desktop](https://desktop.github.com). It's free, works on Mac and Windows, and gives you a visual interface for all of the operations above. Click "Initialize Repository" once at the start; click "Commit" after each iteration; click on a past commit to see what was different. The agent and GitHub Desktop coexist fine — the agent operates on the git data underneath; GitHub Desktop visualizes it. Use whichever you prefer.

## Useful conventions

Once you've decided to use git, a few small conventions make the audit trail much more valuable:

1. **Commit after each iteration round, not after each tiny edit.** Each iteration round is a meaningful checkpoint; each tiny edit is noise. Match the granularity of your `RUBRIC_SCORES.md` entries.

2. **Useful commit messages.** "Update" is not a useful commit message. "Iteration 3: lifted Audience Accessibility from 0.32 to 1.00 by adding chat-vs-agent explainer" is. The agent will write good messages if you ask it to.

3. **Commit your `LOG.md` and `LESSONS_LEARNED.md` along with the work products.** These files are part of the project's history and belong in the same checkpoint as the iteration that produced them.

4. **Don't commit secrets, API keys, or large binary files** without thinking. The repo's `.gitignore` file controls what git ignores. The agent can set up a sensible `.gitignore` automatically if you ask.

## Pushing to a remote (optional)

So far we've talked about git on your local machine. You can also push the project to a private repository on GitHub (free) so that:

- It's backed up off your machine
- You can access it from another computer
- You can share it with collaborators
- You have a permanent record even if your laptop dies

This is also a single-line ask to the agent: *"Push this project to a private GitHub repo named X."* You'll need to be logged in to GitHub from your machine; the agent does the rest.

## When NOT to use git

- One-off chats where you'll never iterate
- Projects where the deliverable is small and the iteration count is 1-2
- Documents you're editing in Google Docs or Microsoft Word with their own version histories (those have built-in revision tracking that may suffice)

For everything else — methodology projects, code, slide decks, research memos, analyses — git pays for itself in the third iteration.

## A starter command sequence (so you've seen it)

If you ever want to do this yourself, the absolute minimum is:

```bash
cd path/to/your/project
git init
git add .
git commit -m "Initial project scaffold"

# ... do work, iterate ...

git add .
git commit -m "Iteration 2: ..."

# ... and so on
```

That's the entire mental model. Five lines. Most knowledge workers can be confident with this in 20 minutes. The agent makes it five lines you don't have to type.

## Resources for going deeper

If you want to actually learn git rather than have the agent do all of it:

- [GitHub's Hello World guide](https://docs.github.com/en/get-started/start-your-journey/hello-world) — the official 10-minute walkthrough
- [GitHub Desktop documentation](https://docs.github.com/en/desktop) — for the GUI app users
- [Pro Git book](https://git-scm.com/book/en/v2) — the canonical free book; chapter 1 is enough for our purposes
- [Atlassian's Git Tutorials](https://www.atlassian.com/git/tutorials) — clean explanations with diagrams

## The 60-second summary

- Git tracks every iteration of your project folder as a checkpoint you can return to.
- The agent runs all the commands. You don't need to memorize anything.
- Use [GitHub Desktop](https://desktop.github.com) if you'd rather click than type.
- Highly recommended, but the method works without it. Skip if you're getting started; add it on your second project.
