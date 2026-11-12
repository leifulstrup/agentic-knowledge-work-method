---
name: init-git-repo
description: Initialize git version control on the current project folder with a sensible .gitignore. Optional but highly recommended companion to `init-knowledge-work-project`. The user does not need to know git commands — this skill runs them. Use whenever the user says "set up git," "initialize version control," "track this with git," "set up checkpoints," or asks about being able to revert changes later.
---

# init-git-repo

## When to invoke
- After `init-knowledge-work-project` has created the folder structure
- Whenever the user says "set up git" or "version control this" or "I want to track changes"
- On project 2+ if the user skipped git on project 1 and wants to add it now

## When NOT to invoke
- If the folder is already a git repo (check for `.git/` first)
- If the user has explicitly said they don't want version control on this project
- If the project is one-off and won't iterate (the discipline doesn't pay back for ≤2-iteration projects)

## What this skill does

Runs `git init` on the project folder, creates a sensible `.gitignore` for knowledge-work projects, makes the initial commit with a useful message, and tells the user what just happened in plain language. The user does not need to know any git commands.

## Steps

1. **Verify** the folder is not already a git repository (check for `.git/` directory). If it is, ask the user before proceeding.
2. **Verify** git is installed (`git --version`). If not, give the user a one-line install instruction for their platform.
3. **Run `git init -b main`** in the project folder.
4. **Create a sensible `.gitignore`** with entries for: `.DS_Store`, common editor temp files, common large/binary files, secrets-shaped patterns (`.env`, `*.key`, `secrets.json`, etc.), Claude Code's local settings (`.claude/settings.local.json`, `.claude/*.local.json`: approved commands are saved there verbatim, inline credentials included), and project-rendered output if applicable (`build/`, `dist/`, `*.pyc`, `__pycache__/`, etc.).
5. **Create a `.gitattributes`** with sensible line-ending handling.
6. **Configure local git identity** if not already configured: `git config user.name` and `git config user.email`. Ask the user for these if missing — set them at the repo level only, not globally, unless the user requests global.
7. **Run `git add -A`** to stage everything except gitignored files.
8. **Run the initial commit** with the message `"Initial scaffold: project folder, templates, intent locked"` (or adapt to project state).
9. **Print a friendly summary** in plain English: what's now tracked, what's ignored, how to commit future iterations (via `commit-iteration` skill), and where the friendly guide lives.

## What NOT to do

- **Do not push to a remote** as part of this skill. That's a separate decision the user makes later.
- **Do not configure GitHub credentials** automatically. If the user wants a remote, that's a follow-up step.
- **Do not assume the user knows git terminology.** Output should be plain language. "Tracked" not "indexed." "Checkpoint" not "commit hash." "Earlier version" not "previous SHA."
- **Do not skip the `.gitignore`.** A repo without `.gitignore` will start tracking junk on iteration two.

## Output format

```
==> Git tracking initialized on <folder>.

  Tracked files: <N> (the project's actual content)
  Ignored: macOS metadata, editor temp files, secrets-shaped files
  Initial checkpoint committed: "Initial scaffold: project folder, templates, intent locked"
  
  Repo identity (this project only):
    Name:  <git config user.name>
    Email: <git config user.email>

==> What this means in plain English:
    Every meaningful iteration can now be saved as a checkpoint you can
    return to later. The next time you finish an iteration round, ask
    me to "commit this iteration" — I'll run the right command and
    write a useful message. If a future revision goes wrong, ask me
    to "show the history" or "revert to the last good version."

==> Friendly intro guide if you want it: guides/05-git-and-version-control.md
==> Next step: continue with the project (clarify-intent or whatever stage
    you're on). git commits happen automatically as you reach iteration
    boundaries.
```

## Operating principles

- **The user shouldn't have to know git** to benefit from it. The agent runs the commands.
- **A `.gitignore` from the start** prevents most beginner footguns (committing secrets, tracking generated files, etc.).
- **Sensible defaults over perfect customization.** The default `.gitignore` should work for 95% of projects. Customize on request, not preemptively.
- **Plain language in output.** "Checkpoint," "history," "revert," "previous good version" — not "commit," "log," "checkout," "HEAD~3."
- **Confirm git identity at repo level.** Setting it globally can surprise users who already have global config; setting at repo level is reversible.
