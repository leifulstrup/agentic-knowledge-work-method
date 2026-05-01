---
name: curate-research-folder
description: Build an annotated Research/ folder for an agentic-knowledge-work project. Combines agent-found sources with the user's own preferred sources. Each source gets a one-line note explaining why it's in the folder. Use after `clarify-intent` and before any work begins. Trigger phrases include "curate research," "build the research folder," "find sources," "what should we read."
---

# curate-research-folder

## When to invoke
- After `clarify-intent` has populated `README.md`
- Before substantive work begins
- When `Research/` is empty or has not been curated

## What this skill does

Builds out the `Research/` folder with three categories of source material:

1. **The user's own seed sources** — preferred references the user already trusts
2. **Agent-found primary sources** — research papers, primary documents, named-publication articles
3. **Best-practice references** — domain conventions, style guides, well-regarded methodology sources

Every item in the folder gets a one-line note in `Research/README.md` explaining why it's there.

## Steps

1. **Read `README.md`** to understand the project's intent, audience, and constraints.
2. **Ask the user for seed sources.** "What are 2-5 sources you already trust on this topic? They can be books, papers, articles, internal documents, or specific people's work."
3. **Save the user's seed sources** to `Research/`. For URLs that the agent can fetch, fetch and save the content. For sources the agent can't access, document the citation in `Research/README.md`.
4. **Identify gaps.** Based on the project's intent, what additional source material would the agent need to do the work well?
5. **Search for those gaps.** Prefer named publications (academic journals, journal of record newspapers, primary documents). Avoid quote-aggregator sites and unattributed Medium posts.
6. **For each found source, add it to `Research/`** with a one-line note in the index.
7. **Update `Research/README.md`** with the full index — file name, source type, why it's here.
8. **Append a structured entry to `LOG.md`** documenting the curation step and the source count.

## Curation rules (enforce strictly)

- **Add only sources that earn their place.** Each must have a one-line justification in the index. If you can't write the line, don't add the source.
- **Prefer primary sources.** A 1925 Fisher paper beats a 2023 blog post citing Fisher.
- **Mix human + agent.** The user's seed sources almost always carry the highest signal. Don't overwhelm them with a long agent-found list.
- **Cite, don't just link.** Each item has author, publication, date.
- **Keep it small.** 5-15 items is normal for a typical project. More than 20 means the folder isn't curated, it's a dump.

## What NOT to do

- Do not add general "background reading." The agent has training data.
- Do not add vendor marketing content unless explicitly requested.
- Do not add anything the user wouldn't actually trust.
- Do not exhaustively search — curate. A small folder of high-signal sources beats a large folder of mid-signal sources.

## Output format

```
==> Research/ curated. <N> items indexed.

  User seed sources: <count>
  Agent-found primary sources: <count>
  Best-practice references: <count>

==> Index in Research/README.md.
==> Logged in LOG.md.
==> Next step: run `build-project-rubric` to create the quality gate
    using the curated sources as ground truth.
```

## Operating principles

- **The user's sources are usually the best sources.** The agent's job is to fill gaps, not replace.
- **A small curated folder beats a large dumped folder.** Discipline pays back during the work.
- **Cite primary, never aggregator.** This single rule eliminates most quote-attribution and stat-citation errors downstream.
