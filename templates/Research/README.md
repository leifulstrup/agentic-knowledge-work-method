# Research Folder
*Curated source material the agent uses as ground truth.*

This folder contains source materials that inform the project — research papers, primary documents, verified quotes, domain best practices, and the project owner's own preferred sources. The folder is curated, not exhaustive. If a source doesn't help the project, it doesn't belong here.

## How this folder is used

The agent reads the contents of `Research/` at the start of each session as ground-truth context. When a question of fact, quality, or convention arises, the agent checks here before guessing or making something up.

## Index

| File | Source type | Why it's here |
|---|---|---|
| *(filename)* | *(book / paper / article / dataset / quote / interview / primary doc)* | *(one-line note on what this source contributes to the project)* |

*(replace with actual sources as the folder fills.)*

## Curation rules

- **Add only sources that earn their place.** Each file has a one-line note in the index above. If you can't justify the note, the source doesn't belong.
- **Prefer primary sources.** Quote-aggregator sites repeat each other; primary documents do not.
- **Mix agent-found + your own.** The agent's research is fine but the highest-value sources are usually the ones you (the human) already trusted before the project started.
- **Cite, don't just link.** Each item has a publication / author / date so the agent can attribute properly when generating work.

## What does NOT go here

- General "background reading" on the topic — the agent has training data
- Vendor marketing content
- Anything the project owner doesn't actually trust
- Files that weren't read or used during the project

When in doubt: leave it out. A small, curated folder beats a large, noisy one.
