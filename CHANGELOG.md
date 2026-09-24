# Changelog

All notable changes to this repo are recorded here. Versions follow [Semantic Versioning](https://semver.org/). The version number lives in [`VERSION`](VERSION) and is tagged in git as `vX.Y.Z`.

## [0.2.0] — 2026-09-24

### Added
- An `examples/` folder with `sample-skills-mined.md`, which is `mine-skills-from-project` output from an MBA case-study project. It shows what a finished skills retrospective looks like: ranked candidates with their evidence, a placement for each, and the candidates it refused.
- `mine-skills-from-project` links to the example again.

### Fixed
- The example's summary said 3 candidates were refused. It now says 2, which matches its list. The third item on that list was the one skipped as already installed.

## [0.1.1] — 2026-09-24

### Fixed
- The README's contents list no longer mentions an `examples/` folder. The folder was never in the repo.
- The README now says the repo has seven core skills plus two optional git skills. It previously said seven, while its skills table listed nine.
- The README now says there are five guides. It previously said four.

## [0.1.0] — 2026-09-24

This is the first versioned release. The number marks the start of versioning, not the method's maturity. The git history before this tag records the earlier work.

### Included
- `METHOD.md`: the full method reference, with the five-file folder, the five-stage loop, and why the method compounds.
- `templates/`: starter files for README, LOG, LESSONS_LEARNED, RUBRIC and Research/.
- `skills/`: seven core Claude Skills plus two optional git skills (`init-git-repo`, `commit-iteration`).
- `guides/`: five how-to guides covering getting started, rubrics, research discipline, skill promotion, and git for non-technical users.

### Changed
- `mine-skills-from-project` was updated to its May 2026 revision. The revision adds a `when_to_use` trigger list, tightened `allowed-tools`, a guard against mining projects that are too sparse, dated output filenames, a check against skills already installed, and a longer edge-cases section. The core method is unchanged.

[0.2.0]: https://github.com/leifulstrup/agentic-knowledge-work-method/releases/tag/v0.2.0
[0.1.1]: https://github.com/leifulstrup/agentic-knowledge-work-method/releases/tag/v0.1.1
[0.1.0]: https://github.com/leifulstrup/agentic-knowledge-work-method/releases/tag/v0.1.0
