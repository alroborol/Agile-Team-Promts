---
name: sprint-review
description: Review the sprint progress and identify any blockers or issues that need to be addressed.
---
# Sprint Review - AI-Driven Insights

## Input
- Review progress.md for sprint activities and outcomes

## Analysis
- Extract completed tasks and story points from `progress.md`
- Normalize records by Sprint-ID and Task-ID before aggregation; do not merge entries from different sprint cycles that reuse task labels.
- Compare delivered work against the original sprint brief in `sprint.md`
- Classify each completed task as implementation, verification-only, or mixed when comparing planned work to delivered work
- Detect status mismatches between `sprint.md` and the latest relevant `progress.md` session; classify any mismatch as High severity.
- Identify inefficiencies in task execution.
- **Identify repeated failure patterns across tasks, not just isolated blockers:**
  - Group failures by root cause category: Process/Tooling (config, discovery, formatting) vs. Product/Feature (logic defects, missing behavior) vs. Documentation (mismatches, missing criteria)
  - For each repeated pattern, count occurrences and note the missing control that would have prevented each recurrence
  - Distinguish between process friction (zero feature cost, preventable by config/tooling) and product defects (require code fixes)
- Summarize each repeated failure pattern by root cause, control absence, and severity
- Review prompts under `.github/prompts/` to identify missing guidance that contributed to inefficiencies.
- Propose exact prompt edits to prevent future recurrence of same-root-cause failures

## Key Findings
- Actual work vs. planned work
- Include a required table with: Task, Planned Type, Delivered Type, Story Points, Current Status, and Delta Reason.
- Insufficiencies in prompts
- Missing metrics or controls that prevented accurate sprint reporting
- Task-level root causes for repeated gate failures or verification-only work

## Recommendations
- Sprint process improvements
- Prompt improvements
- If the prompts are missing required controls, propose exact edits to the affected prompt files
- If test readiness differs between scoped and unscoped pytest runs, include a clear release verdict and the gating policy used.
