# Project Rubric
*Quality gate the agent uses to self-evaluate before declaring work "done."*

This rubric is project-specific and updated as new failure modes surface. The structure has two layers:

- **Big-picture (first principles):** does the work answer the question we set out to answer? Does it serve the audience and the intent?
- **Tactical (quality):** are the artifacts actually well-made — readable, sourced, accessible, free of avoidable defects?

Score each criterion 0-4. Any 0 is disqualifying — the work cannot ship until the 0 is resolved.

---

## Dimension 1 · First-principles tests

| # | Criterion | Weight | What "exemplary (4)" looks like |
|---|---|:---:|---|
| F1 | **Intent satisfied** | 15% | The work delivers on the project's stated intent in `README.md`. Anyone reading the work can identify the intent without being told. |
| F2 | **Audience-fit** | 15% | The work is calibrated to the named audience — language, depth, examples, format. A different audience would have produced a different artifact. |
| F3 | **Source integrity** | 10% | Every claim that requires a source has one. Quotes are verbatim and traced to primary sources. Stats have publication, date, and citation. |

## Dimension 2 · Tactical-quality tests

*(replace these with criteria specific to your project type — slides, docs, code, etc.)*

| # | Criterion | Weight | What "exemplary (4)" looks like |
|---|---|:---:|---|
| T1 | **Renders correctly** | 10% | All artifacts produce the expected output when rendered, compiled, or executed. No layout breaks, no broken images, no failed builds. |
| T2 | **Readable / accessible** | 10% | Visuals pass the audience's reading conditions (projector, mobile, print). WCAG AA contrast on slides; clear formatting on docs; comments + tests on code. |
| T3 | **Specificity** | 10% | Where the work makes a claim, the claim is specific — named, sourced, dated — rather than generic. |

## Dimension 3 · Project-specific criteria

*(add your own — this section will likely grow as you discover failure modes. Each criterion that gets added here came from a real moment when something almost shipped that shouldn't have.)*

| # | Criterion | Weight | What "exemplary (4)" looks like |
|---|---|:---:|---|
| P1 | *(add as you go)* | — | — |

---

## Disqualifying failure modes

The work cannot ship if any of the following are true. Add to this list as you discover new failure modes mid-project:

- An attributed quote has no primary source
- A statistic is cited without a publication and date
- A claim that hits a 0 on F1 (the work doesn't actually satisfy the intent)
- *(add project-specific disqualifiers here)*

---

## How to apply this rubric

1. **First pass — after the first complete draft.** Run all criteria. Surface gaps. Don't try to fix yet — just inventory what failed.
2. **Iteration passes — after each substantive revision.** Re-score the dimensions you touched.
3. **Final pass — before declaring done.** All criteria, no 0s allowed. If any criterion is at 0, the work is not done.

The rubric is a living document. When you find a failure mode in the work that wasn't in the rubric, add it. The rubric inherits the lesson permanently.
