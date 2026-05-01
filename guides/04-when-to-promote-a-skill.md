# When to Promote a Skill From Project-Local to System-Wide
*The decision rule for where Claude Skills should live.*

Claude Skills can live in two places:

- **`PROJECT/.claude/skills/`** — project-local, only loaded when the agent is working in that specific project folder
- **`~/.claude/skills/`** — system-wide, loaded for every Claude session you run

Knowing where to put a new skill is a small but high-leverage decision. Project-local first, system-wide after the skill has earned its place. Here's the rule.

## Default to project-local

When `mine-skills-from-project` proposes a new skill, default to project-local placement. Three reasons:

1. **Skills mature.** A skill that just got proposed is a draft. The first version is rarely the final version. Keeping it project-local lets you iterate without it leaking errors into other projects.
2. **Domain specificity.** Many skills initially feel general but turn out to be tied to a domain. A "build the headline-wall slide" skill is great for talks; useless for code review.
3. **Discoverability.** A system-wide skill folder full of half-finished or domain-narrow skills creates trigger-collision problems where the wrong skill activates.

## Promote to system-wide when three are true

A skill earns system-wide placement when **all three** of these are true:

### 1. It has been used in 2-3 projects across different contexts

A skill used only in one project is, by definition, project-specific. A skill used across two or three different project types is showing genuine generality.

### 2. It has a clean, unambiguous trigger

The skill activates when the right phrase appears and only when it should. If you've seen it accidentally trigger on unrelated work, the trigger needs refinement *before* promotion.

### 3. It produces consistent, useful output across users / contexts

If the skill works well for your slide projects but breaks on someone else's, or if it produces good results for one writer's voice but jarring results for another's, it's not yet generalizable. Often the fix is to make the skill ask 1-2 clarifying questions upfront.

If any of the three is missing, leave it project-local for now.

## What system-wide skills look like

The strongest system-wide skills tend to be:

- **Workflow scaffolds** — `init-knowledge-work-project`, `clarify-intent`, `mine-skills-from-project`. These work across virtually any project.
- **Format converters** — extract speaker notes from a Marp deck, convert markdown to PowerPoint, etc.
- **QA / QC tooling** — `marp-deck-qc`, `quote-verifier`, accessibility checkers. The output is uniform regardless of the project's domain.
- **General research helpers** — `curate-research-folder`, `headline-pack-builder`. Domain-agnostic if written carefully.

## What stays project-local

- **Domain-specific templates.** An organization-specific slide theme — pre-set with brand colors, fonts, and slide layouts — stays project-local (or moves to a shared theme-pack plugin if shared with colleagues at the same organization).
- **Codebase-specific helpers.** A skill that knows your billing system's column names belongs in that codebase's `.claude/skills/`, not system-wide.
- **One-off automation that's still maturing.** When in doubt, project-local.

## How to promote

When all three promotion criteria are met:

1. **Test the skill in isolation.** Trigger it deliberately and confirm output quality.
2. **Test it with collision risk in mind.** Are there other skills in `~/.claude/skills/` that might accidentally fire on the same trigger? If so, refine the trigger phrase.
3. **Move the skill folder** from `PROJECT/.claude/skills/<skill-name>/` to `~/.claude/skills/<skill-name>/`.
4. **Update any references.** If the skill is referenced from documentation or other skills, update the path.
5. **Run the skill on a different project's context** to confirm it works outside its origin context.
6. **Document the promotion** in a skill-history log if you keep one.

## How to demote

Demotion is rare but valid. If a system-wide skill turns out to:

- Trigger on too many false positives
- Produce inconsistent output for some project types
- Be obsoleted by a better skill

…move it back to project-local in the projects that genuinely need it, and remove from system-wide.

## Maintenance discipline for `~/.claude/skills/`

System-wide skills accumulate. Every 6 months, prune:

- Skills that haven't been triggered in 6+ months are candidates for archive
- Skills with overlapping triggers should be merged
- Skills that produce inconsistent output should be revised or demoted

A 50-skill `~/.claude/skills/` directory you actively use is fine. A 200-skill directory where most are stale is worse than a 20-skill curated set.

## The plugin path (when skills graduate beyond personal use)

When a coherent set of related skills has matured to system-wide quality and would be useful to colleagues or the broader community, consider packaging them as a Claude Skills *plugin*:

- A plugin bundles related skills, templates, and themes into a single installable unit
- Plugins are versioned and shareable
- Other people can install your plugin into their `~/.claude/skills/` with a single command

The slide-deck workflow (Marp theme + headline-wall builder + speaker-notes extractor + bio-attribution-slide builder + quote-verifier-extension) is a natural plugin candidate. The agentic-knowledge-work method itself (the seven starter skills in this repo) is another.

But that's an advanced step. Most skills will live their entire useful life as project-local or personal-system-wide. Plugins are for skills that have proven themselves across many projects and many users.
