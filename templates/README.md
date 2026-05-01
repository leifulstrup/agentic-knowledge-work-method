# Project Templates
*Drop-in starter files for any new agentic-knowledge-work project.*

## How to use

Copy these four files plus the `Research/` folder into the root of a new project:

```bash
cp -r templates/* path/to/your-new-project/
```

Then customize each one:

- **`README.md`** — replace the placeholders with your project's actual intent, audience, deliverable, and deadline. This is the file the agent reads first to understand what you're trying to do.
- **`LOG.md`** — leave it nearly empty; the agent appends as the project progresses.
- **`LESSONS_LEARNED.md`** — leave it nearly empty; capture lessons mid-project, not at the end.
- **`RUBRIC.md`** — start with the generic rubric; replace or extend with project-specific criteria as you go. The rubric is a living document.
- **`Research/README.md`** — when you start curating sources, this index file documents what's in the folder and why.

## Why this set, and only this set

The five files (plus Research/) are the minimum viable working memory for an agent on a real project. Fewer than this and you re-explain context every session. More than this and the agent starts guessing about which file to read.

Every file has one job:

| File | Job |
|---|---|
| `README.md` | What is this project? What does done look like? |
| `LOG.md` | What did we do, in what order, with what result? |
| `LESSONS_LEARNED.md` | What did we *learn* — distilled, durable, transferable? |
| `RUBRIC.md` | How do we know the work is good? |
| `Research/` | What sources do we trust as ground truth? |

If you find yourself adding more files, ask whether they belong in one of the five or in `work products/`. Almost always, they do.

## Optional: put the folder under version control

Once you've copied the templates and started filling them in, **highly recommended (but optional):** initialize git tracking on the project folder. Each iteration becomes a checkpoint you can revert to. The agent runs every git command for you — you don't need to know the command line. Read [`../guides/05-git-and-version-control.md`](../guides/05-git-and-version-control.md) for a non-technical introduction. Skip git on your first project if it feels like too much; add it on your second.

## What each file should NOT do

- `README.md` is not a status report. Status goes in LOG.md.
- `LOG.md` is not a polished narrative. It's a working log; messy is fine; "wrong turns" should be visible, not hidden.
- `LESSONS_LEARNED.md` is not a tweet thread. Each entry is two or three paragraphs.
- `RUBRIC.md` is not a checklist of generic best practices. It is project-specific and updated when you find new failure modes.
- `Research/` is not a link dump. Each item has a short note explaining why it's in the folder.
