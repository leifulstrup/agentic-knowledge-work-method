---
name: clarify-intent
description: Run a structured Q&A loop with the user to lock the project's intent, audience, deliverable, deadline, and constraints before any work begins. Use immediately after `init-knowledge-work-project`, or whenever the user is starting work but the README.md is still placeholder content. Trigger phrases include "clarify intent," "lock the brief," "what are we trying to do," "before I start," "set the goal."
---

# clarify-intent

## When to invoke
- Right after `init-knowledge-work-project`
- Whenever `README.md` has placeholder content
- When the user starts asking the agent to do work but the success criteria are vague

## What this skill does

Walks the user through a structured intake interview that produces a fully-populated `README.md`. The interview is **specific and short** — five categories, three to five questions per category, no more.

The output is a `README.md` the agent can rely on as ground truth for the rest of the project.

## The five categories

### 1. Intent (what are we trying to accomplish?)

- What is the *single sentence* that describes what this project produces?
- What is the *underlying need* this project is responding to — what would happen if we did nothing?
- What does success look like, *concretely*? Not "good slides" — "slides that the audience can recall the central claim of three weeks later."

### 2. Audience (who is this for?)

- Who is the named audience or beneficiary? (Not a category — actual humans, with names or roles.)
- What do they already know about the topic?
- What's their attention budget — how long will they engage with the artifact?
- What is the *worst* misreading they might have, and how do we prevent it?

### 3. Deliverable (what's the actual artifact?)

- What format? (slides / report / spreadsheet / code / decision memo / something else)
- Where does the deliverable live when finished — what's the destination platform or context?
- Are there technical constraints? (page limit, slide count, codebase conventions, brand guidelines)

### 4. Deadline (when is this due?)

- What's the hard deadline?
- What's the bar for "done enough to ship"?
- What's the bar for "good enough to be proud of"?

### 5. Constraints (what should the agent know upfront?)

- Domain conventions or regulatory considerations
- Audience sensitivities
- Brand or stylistic constraints
- Confidentiality boundaries
- Time the user can invest in this project (their own time, separate from the deadline)

## Steps

1. **Open the user's `README.md`** to see what's already there.
2. **Walk the five categories** one at a time. For each, ask the questions; capture answers concisely; do not move to the next category until the current one is complete.
3. **Restate** the user's answers back in your own words after each category to confirm understanding.
4. **Update `README.md`** with the answers, organized by category.
5. **Append a structured entry to `LOG.md`** documenting that intent was clarified (with timestamp and the agreed success criteria).
6. **Print a summary** showing the populated README and confirming the next step.

## What NOT to do

- Do not skip categories because the user has already mentioned something. Ask explicitly even if you think you know the answer.
- Do not let the user leave the interview with vague success criteria. "Good slides" is not a success criterion. "Audience recalls the central claim three weeks later" is.
- Do not write the README from your own assumptions. Every line in the README should be traceable to a specific user response.
- Do not start work after the interview unless the user explicitly says "let's begin."

## Output format

After the interview completes:

```
==> Intent locked. README.md updated.

  Project: <name>
  Intent: <one sentence>
  Audience: <named>
  Deliverable: <format + destination>
  Deadline: <date + bar>
  Constraints: <list>

==> Logged in LOG.md.
==> Next step: run `curate-research-folder` to build out Research/
    with the sources we'll rely on.
```

## Operating principles

- **Better to spend 30 minutes here than 30 hours later.** Vague intent is the most common reason agent work goes off the rails.
- **The user's own words go in the README, not the agent's paraphrase.** Trust the user to articulate what they want; the agent's job is to ask the right questions, not generate the answers.
- **One pass is enough.** Don't re-clarify the same intent throughout the project. If the intent shifts, that's a real event — log it in LOG.md and update the README explicitly.
