# Research Folder Discipline
*Curated, not exhaustive. Trusted, not abundant.*

The `Research/` folder is the agent's ground-truth context. It is *not* a list of links. It is a curated set of source material the project actually relies on.

## The single rule

> If you can't write a one-line note explaining why a source is in the folder, the source doesn't belong in the folder.

That rule alone solves 80% of `Research/` problems.

## What goes in

Five categories:

1. **Primary sources** — original research papers, books, named-publication articles, primary documents
2. **Verified quotes with citations** — a quote-pack file with attribution, date, source URL, and rhetorical purpose
3. **Domain best practices** — well-regarded methodology guides for the deliverable type
4. **The user's own seed sources** — references the user already trusts
5. **Recent news headlines** (when relevant) — pulled from named publications, dated, with URLs

## What does NOT go in

- General "background reading" — the agent has training data
- Quote-aggregator sites (azquotes, brainyquote, quotefancy) — they repeat each other and many quotes are paraphrases or misattributions
- Vendor marketing content unless explicitly requested
- Anything the user wouldn't actually trust
- Files the project doesn't actually use

When in doubt: leave it out. A small high-signal folder beats a large noisy one.

## How to organize

The folder has a `Research/README.md` that indexes everything. Format:

```markdown
| File | Source type | Why it's here |
|---|---|---|
| machlup-1962.pdf | Book | Coined "half-life of knowledge" — used on Slide 2 |
| ieee-spectrum-1966-technical-obsolescence.pdf | Magazine article | Original 35-year/10-year engineering half-life numbers |
| nyt-1991-engineer-supply-affects-america.pdf | Newspaper | Updated half-life to <5 yrs engineering, <3 yrs software |
| kruchten-2008-half-life.pdf | Magazine article | 2008 update on software-engineering half-life |
```

Each row is a single source with a one-line rationale. If the rationale is hard to write, the source doesn't belong.

## The quote-pack discipline

For projects that include attributed quotes (slides especially), maintain `quote-pack.md` separate from the rest of the research. Format:

```markdown
## Q1 · Pasteur — preparation creates the surface area for luck

> "In the field of observation, **chance favours only the prepared mind.**"

**Source.** Louis Pasteur, inaugural address as Professor and Dean of the new Faculté des Sciences, Université de Lille, 7 December 1854.

**Why it lands here.** *(rhetorical purpose for the project)*

**URL or full citation for verification.** *(link or page reference)*
```

Rule: **no quote ships in a deliverable that isn't in `quote-pack.md`**. This single discipline eliminates almost all attribution errors.

## The "primary source" rule

A primary source is the *originator* of a claim, fact, or quote. A secondary source cites the primary.

Example:

- *Primary:* the original 1925 R. A. Fisher paper introducing inferential statistics
- *Secondary:* a 2023 textbook discussing Fisher's framework
- *Tertiary:* a Medium post citing the textbook

For the `Research/` folder, prefer primary. When primary is unavailable, secondary is acceptable if you note it explicitly. Tertiary should not appear unless flagged as a research lead, not a citation.

This sounds pedantic. It isn't. The single most common failure mode in agent-generated work is citing a quote-aggregator site as if it were authoritative. The discipline catches that.

## When to add sources mid-project

- A new factual question came up that the existing sources don't answer
- A claim in the work needs a stronger source than what's already in the folder
- The user mentions a source they trust that wasn't added at kickoff

When *not* to add sources:

- The agent found something interesting but it's not actually used in the work
- Background reading the user might want someday but doesn't need now
- Tertiary sources

If you find yourself adding sources you won't actually use, you're hoarding, not curating.

## The "fresh news" subfolder

For projects that reference current events (a talk, a memo, a market analysis), keep current-news headlines separate from durable research:

```
Research/
├── README.md
├── primary-sources/
│   ├── (durable research)
│   └── ...
├── headlines/
│   ├── headlines-pack.md  # ranked list of recent headlines with publication, date, URL
│   └── ...
└── quote-pack.md
```

Headlines have a half-life of weeks. Primary sources have a half-life of years. Don't mix them.

## The compounding effect on Research/

After multiple projects in similar domains, you'll notice the same primary sources recurring. Promote them.

Create a `~/research-library/` directory in your home folder with subdirectories per domain (`statistics/`, `economics/`, `presentation-design/`, etc.). Symlink (or copy) recurring sources into the project's `Research/` folder rather than re-downloading.

Over time, the library becomes valuable in its own right — your personal canon of trusted sources, curated and indexed.

## What good looks like

A well-curated `Research/` folder for a typical knowledge-work project has:

- 5-12 items total
- 1-3 of the user's own seed sources
- 3-7 primary sources (papers, books, primary documents)
- 1-3 best-practice references
- A `quote-pack.md` if quotes are involved
- A `headlines-pack.md` if current events are involved
- A `README.md` index where every entry has a one-line rationale

If you're under 5 items, you may have under-researched. If you're over 15, you may be hoarding. Curate, don't accumulate.
