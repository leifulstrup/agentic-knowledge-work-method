---
name: log-step
description: Append a timestamped entry to LOG.md after a meaningful action. Captures what was done, what happened, and any decisions made. Use after every substantive step in a project — not after every chat message, but whenever something shipped, broke, was decided, or surprised the user or agent. Trigger phrases include "log this," "note this in the log," "update the log," "session note."
---

# log-step

## When to invoke
- After completing a meaningful action (a draft was written, a render succeeded, a decision was made, a problem was found and fixed)
- At the end of a working session, to summarize what happened
- When the user explicitly asks for a log update

## When NOT to invoke
- After every chat message — the log is for *meaningful* steps, not every back-and-forth
- For purely conversational exchanges (clarifying questions, vibes-checks)

## What this skill does

Appends a structured entry to `LOG.md`. Uses the format:

```markdown
---

## YYYY-MM-DD — Session N · Block label

### Context
*(what was the state of the project at the start of this block)*

### Actions taken
1. *(action — what we did)*
2. *(action)*

### Outcomes
- *(what happened — including problems, fixes, surprises)*

### Decisions
- *(decision + reason, if any decisions got made)*

### Files updated
- *(filename — short note on what changed)*
```

## Steps

1. **Read the current `LOG.md`** to determine the next session number and timestamp.
2. **Capture the action concisely.** Use bullets, not paragraphs. The log is a working record, not a narrative.
3. **Be honest about wrong turns.** If we tried something and it didn't work, log it that way. The "what didn't work" is often more valuable for future reference than the "what worked."
4. **Capture decisions explicitly.** If a choice was made (which slide to cut, which framework to use, which person's feedback to weight), name it and the reason.
5. **Reference specific files.** When a file changed, name the file and what changed in one line.
6. **Append the entry** to `LOG.md`.
7. **Print a one-line confirmation** that the log was updated.

## Format conventions

- **Timestamps in YYYY-MM-DD** — chronological sort works
- **Session numbers reset to 1 for each new project** — but increment within a project
- **Block label** is a short descriptor: "Discovery," "First draft," "Revision after user feedback," "Final QC"
- **Actions in numbered list** — they happen in order
- **Outcomes in bulleted list** — they describe state, not sequence

## What NOT to do

- Do not embellish. The log is a working record, not a polished narrative.
- Do not skip wrong turns or failed attempts. They are the highest-signal entries for future reference.
- Do not log every chat message. The log is for meaningful steps only.
- Do not write paragraphs in any field. Bullets only.

## Output format

After appending:

```
==> LOG.md updated. Session N · <block label>.
    <count> actions, <count> outcomes, <count> file updates.
```

## Operating principles

- **Honest beats polished.** Wrong turns are the asset.
- **Specific beats general.** Name files. Quote specific decisions. Don't summarize away the texture.
- **Brief beats verbose.** A log full of paragraphs is unreadable a week later.
- **Pair with `commit-iteration` if git is initialized.** A LOG.md entry and a git checkpoint at the same iteration boundary produce a complete audit trail. The log explains; the git history captures the full state. Both serve different needs.
