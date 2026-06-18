---
name: sprint-plan
description: Break down sprint board items into adaptable, testable tasks
---

# Purpose
Decompose sprint board items into smaller, testable, and completable tasks with clear acceptance criteria. Progress is measured by working software, not plans.

# Core Principles
- **Adaptive Planning**: Plans evolve based on feedback and learnings
- **Continuous Delivery**: Prioritize working increments over comprehensive upfront design
- **User-Centric**: Shorten the feedback loop between team and stakeholders
- **Explicit Scope Control**: Every task must trace back to a requirement in `sprint.md`
- **Current-State Validation**: Check the repository before planning implementation work; if a requirement is already satisfied, plan verification or traceability work instead of duplicating implementation
- **Explicit Dependencies**: Identify true sequencing constraints; document blocking chains plainly
- **Single Source of Truth**: Store broken-down tasks only in `sprint.md` as a new sprint section; do not create `progress.md` or any separate tracking file

# Pre-Sprint Configuration Audit
Before task breakdown, validate repository configuration to prevent discovery and formatting friction:
- ✓ **Pytest Discovery**: If non-sprint helper modules exist in repository root (e.g., test_generator.py, test_utilities.py), verify `pytest.ini` exists with `testpaths = tests` constraint. If missing, add pytest.ini before sprint execution to prevent High-severity discovery blockers.
- ✓ **Line-Length Configuration**: If both Black and Flake8 are active, verify `.flake8` or `pyproject.toml` has `max-line-length = 88` to match Black default. Black default is 88; Flake8 default is 79. Without alignment, expect repeated E501 rework cycles during task execution.
- ✓ **Documentation vs. Repository**: Verify README.md, CHANGELOG.md, and sprint.md do not claim features that cannot be validated from current workspace contents.
- ✓ **CI/CD Gate Prerequisites**: Document gate order (e.g., build before twine check) and confirm supporting files exist (setup.py, pyproject.toml, pytest.ini).

# Task Requirements
- **Clear Definition**: Specific, measurable, achievable outcomes
- **Working Product**: Codebase remains functional and deployable at all times
- **Prioritized**: Ordered by business value and dependencies
- **Requirement Mapping**: Every task must map back to a specific item in `sprint.md`
- **Size Estimation**: Every task must include story points or t-shirt size estimate
- **Traceability**: Document external dependencies; prefer async interfaces where possible
- **Acceptance Criteria**: Each task must have verifiable pass/fail outcomes
- **Non-Goals & Deferred Scope**: Record explicitly what is excluded or deferred so requirements do not disappear silently
- **Blocking Chains**: Identify and document sequential task dependencies; do not claim parallel execution without justification

# Planning Output
Write the plan directly into `sprint.md` as a new sprint section.
Assign a unique Sprint-ID to the section and require downstream `progress.md` sessions to reference it.
For each planned task, provide:
- Task title
- Requirement mapping (specific reference to `sprint.md` item)
- Planned execution type: implementation, verification-only, or mixed
- Story points or size estimate
- Blocking dependencies and sequencing constraints
- Acceptance criteria
- Non-goals or deferred scope
- Status, blockers, and learnings as the sprint progresses

# Review Guardrails
- If a requirement in `sprint.md` is not covered by any task, call it out explicitly.
- If a task adds scope not present in `sprint.md`, label it as scope expansion and justify it.
- If a requirement is already implemented in the repository, do not treat it as new implementation work; record the task as validation-only or remove it from the sprint breakdown.
- If task labels are reused across sprints, Sprint-ID must disambiguate all references in `progress.md`.
- If tasks are sequential, document the blocking chain plainly instead of claiming parallel execution.
- If any scope from `sprint.md` is deferred, record it in the Non-Goals section.
- Do not create `progress.md`; all task breakdown and tracking must remain in `sprint.md`.

# Quality Gates
✓ Rapid feedback loops
✓ Reduced implementation risk
✓ Scope traceability preserved
✓ Dependencies and blocking chains made explicit
✓ No silent requirement gaps or deferred scope
✓ Broken-down tasks stored only in `sprint.md`

# Key Files
- `sprint.md`: Sprint scope, high-level items, and the broken-down tasks for the new sprint
