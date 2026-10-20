# Open Context Article Reader Initial Skill Implementation Plan

> For agentic workers: implement the tasks in order and validate each deliverable before claiming completion.

**Goal:** Initialize a standalone, usable Agent Skill for understanding one blog post or web article.

**Architecture:** The repository root is the skill folder. `SKILL.md` contains triggering conditions and the reading workflow; `references/` holds method details. Repository documentation records scope, usage, and handoff. No service, vault adapter, or scraper is required.

**Tech stack:** Markdown and YAML frontmatter; Codex Skill Creator validator for structural checks.

**Spec:** `docs/design.md` (copied from the Open Context Forge transition draft and then maintained here).

## Global constraints

- Input is one blog post or web article, supplied as a URL, text, Markdown, or readable local text file.
- Initial domains include technology, business, and philosophy; article function and information quality are separate dimensions.
- Keep source claims, analyst inference, external research, and unknowns distinct.
- Do not depend on or write to Open Context Forge vault; books, long courses, and full academic papers are outside this workflow.

## Task 1: Establish the repository

**Files:** `README.md`, `AGENTS.md`, `docs/HANDOFF.md`, `docs/design.md`

- [x] Confirm the cloned GitHub remote, empty starting state, and branch.
- [x] Copy the design draft into `docs/design.md` and make it the new repository's maintained specification.
- [x] Write README with scope, inputs, example invocation, and current limitations.
- [x] Write AGENTS.md with repository boundaries and validation expectations.
- [x] Write HANDOFF.md with observed state, decisions, and follow-on work.
- [x] Check internal links and repository status.

## Task 2: Implement the reading Skill

**Files:** `SKILL.md`, `references/methodology.md`

- [x] Draft `SKILL.md` frontmatter with a precise trigger and exclusions.
- [x] Define input acquisition, article classification, claim/structure analysis, optional targeted research, and source labeling in the body.
- [x] Put method selection and domain-specific lenses in `references/methodology.md`.
- [x] Run `quick_validate.py` on the repository root and correct structural errors.

## Task 3: Verify representative behavior

**Files:** `docs/HANDOFF.md` (record results)

- [x] Test a technical tutorial, business argument, philosophy essay, and article with missing background or weak evidence.
- [x] Test a URL that cannot be read and a request for a book; confirm that the Skill reports the boundary instead of inventing content.
- [x] Check that outputs identify the author's actual question and thesis, adapt to article function, and label unsupported inferences.
- [x] Run whitespace/link checks and record remaining limitations in HANDOFF.md.

## Completion boundary

Local files and verification are in scope. An initial commit and push may follow once the contents are reviewed. Repository visibility remains private until the user separately requests publication.
