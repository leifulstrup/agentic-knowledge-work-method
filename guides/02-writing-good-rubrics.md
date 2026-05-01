# Writing Rubrics That Actually Catch Issues
*The rubric is your quality gate. This guide is how to make one that works.*

A bad rubric is a list of generic best practices that always pass. A good rubric is a project-specific quality gate that catches the failure modes you've actually seen — yours and the agent's.

## The two failure modes of rubrics

**Failure mode #1: Too generic.** "Slides are well-designed." This catches nothing. Every slide can be argued to meet this bar.

**Failure mode #2: Too long.** A 30-criteria rubric is a checklist. The agent (and you) start gaming it.

The sweet spot is 8-12 criteria, organized into 2-3 dimensions, where every criterion names a specific failure mode you've seen before.

## The three-dimension structure

Every rubric I write has the same three dimensions:

### Dimension 1 · First-principles tests (30-40% weight)

Does the work answer the question we set out to answer? Does it serve the named audience? Does it survive a credibility check?

Example criteria:

- **Intent satisfied.** "The work delivers on the project's stated intent in `README.md`. Anyone reading the work can identify the intent without being told."
- **Audience-fit.** "The work is calibrated to the named audience — language, depth, examples, format. A different audience would have produced a different artifact."
- **Source integrity.** "Every claim that requires a source has one. Quotes are verbatim and traced to primary sources."

These are stable across projects. They rarely change.

### Dimension 2 · Tactical-quality tests (30-40% weight)

Are the artifacts actually well-made? Readable, accessible, free of avoidable defects?

These criteria are deliverable-type-specific:

- **For slides:** rendering correctness, readability at 1280×720, WCAG AA contrast, glance test, no overflow
- **For reports:** structure, citation density, copy-edit quality, exec-summary accuracy
- **For code:** tests pass, lint clean, security scan clean, complexity bounds, docstrings present
- **For analyses:** data lineage, methodology documentation, reproducibility, sensitivity analysis

Pick a starter set from the templates and adapt to your specific deliverable.

### Dimension 3 · Project-specific criteria (20-40% weight)

This is where the rubric becomes valuable. These criteria come from the specific failure modes of *this* project.

Examples from real projects:

- *(slide deck for a graduating MS class)* "International student reality named directly. 58% of audience is international; STEM OPT and H-1B come up. Silence on this is failure."
- *(code refactor of a billing system)* "All currency math uses Decimal, never float. Any float-typed variable in money-handling code is disqualifying."
- *(client board memo)* "No information attributable to other clients. Read every example and confirm it could be public, or disguise."

Dimension 3 starts empty and grows as you discover failure modes. **The discipline:** every time something almost shipped that shouldn't have, write a criterion that catches that failure mode in the future.

## How to set weights

Weights matter when you're tracking improvement across iterations. Total to 100%. Default starting point:

- Dimension 1 (first-principles): 40%
- Dimension 2 (tactical): 40%
- Dimension 3 (project-specific): 20%

Adjust as the project reveals its center of gravity. For a deck where audience-fit is the whole game, weight Dimension 1 more heavily. For a code project where security and tests matter most, weight Dimension 2 heavier and add specific criteria.

## How to write a criterion

Three-part structure:

1. **Name** — short, memorable (e.g., "Citation discipline," "Audience-fit")
2. **Weight** — percentage points
3. **Exemplary description** — what does a 4-out-of-4 look like, concretely?

The exemplary description is where most rubrics fall apart. "High quality" is not a description. "Every cited stat has a publication, date, and primary-source URL on the slide itself" is.

### Bad criterion

> Source quality | 10% | Sources are good

### Good criterion

> Source integrity | 10% | Every quote is verbatim and traces to a primary source documented in `quote-pack.md`. Every statistic has publication, date, and URL on the slide. Zero use of aggregator-site quotes (azquotes, brainyquote, etc.).

The good criterion is operational. The agent (and you) can apply it in seconds and produce a defensible 0-4 score.

## The disqualifier list

Any single criterion at 0 disqualifies the whole work. The disqualifier list at the bottom of `RUBRIC.md` is the explicit catalog of "0 = cannot ship" rules. Examples from real projects:

- An attributed quote has no primary source
- A statistic has no publication and date on the slide
- The deliverable doesn't actually answer the question in the README
- An accessibility check fails (contrast below WCAG AA, code without docstrings, etc.)
- A claim the user can't defend made it onto the slide

When you find a new disqualifier mid-project, add it to the list. The rubric inherits the lesson permanently.

## How to use the rubric during the project

Three pass cadence:

1. **Pass 1 — after the first complete draft.** Score every criterion. Don't try to fix yet — inventory what failed. This is diagnostic.
2. **Pass 2 — after each substantive revision.** Re-score the dimensions you touched. Watch the score climb.
3. **Pass 3 — final, before declaring done.** All criteria. No 0s allowed. If any criterion hits 0, the work is not done.

The rubric isn't a one-time form to fill out. It's the gate the agent (and you) check against every time something is "ready."

## Common rubric mistakes

- **Adding a criterion that doesn't have a clear "exemplary" description.** If you can't describe what 4-out-of-4 looks like, the criterion will produce inconsistent scores.
- **Adding criteria for things you can't actually evaluate.** "Audience will recall this in three weeks" — you can't measure this. Replace with: "The S.T.A.R. moment is a single sentence the agent or user can paraphrase verbatim after one read."
- **Treating the rubric as locked after creation.** Rubrics grow. Dimension 3 in particular. Plan for it.
- **Letting the rubric balloon.** When you hit 15+ criteria, prune. Combine related criteria. Drop the weakest. The rubric should fit on one screen.

## Example: how a rubric evolved across a real project

A guest-lecture project I ran with this method started its rubric with 17 criteria across 3 dimensions, weighted: 30% craft / 25% voice / 45% audience resonance. Dimension 3 (audience resonance) had 11 criteria, the most-weighted dimension because the talk's failure mode was "great deck for the wrong room."

Mid-project, when the host gave feedback that the audience had less management experience than initially assumed, two new criteria entered Dimension 3:

- "Calibrated to early-career stage — no management presumption"
- "Technical specificity respected"

Both came from real failure modes in the working draft. Both stuck.

By the end, the rubric had caught and prevented multiple "almost shipped a problem" moments. That's what a working rubric does.

## Final principle

A rubric is a contract between you and the agent about what "done" means. Vague contracts produce inconsistent work. Specific contracts produce work the agent can self-evaluate against. Spend the 20 minutes upfront. Save the hours of rework.
