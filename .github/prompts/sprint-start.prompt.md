---
name: sprint-start
description: Handle sprint.md tasks, report progress in progress.md, summarize in kpt.md.
---

## Workflow
1. Pick a TODO task from sprint.md with no session ID
2. Atomically mark as DOING, append your session ID
3. Record progress in progress.md (level 2 heading with session ID prefix) and include Sprint-ID + Task-ID metadata in the section body
4. Document plan, requirement mapping, size, acceptance criteria, and non-goals
5. Add discovered dependencies/refactoring to progress.md backlog
6. Run a fast local check first: formatting/lint on changed files and any task-specific smoke checks
7. Before editing, verify formatter and linter constraints for the touched files; if black and flake8 disagree, record the active line-length policy and wrap conservatively
8. Verify gate prerequisites before the full CI/CD bundle (for example, build artifacts before packaging checks)
9. Run CI/CD and document results, including any rework caused by failures
10. If the same gate fails more than once for the same root cause, record it as a repeated process issue and the preventative control that should avoid recurrence
11. Record planned-vs-actual deltas, including unmet original requirements or scope expansion
12. **Track token usage** (input/output tokens consumed) in progress.md for cost analysis; if unavailable, record N/A and the telemetry/tooling limitation explicitly
13. Mark task DONE (if CI/CD passes) or TODO (remove session ID) in sprint.md
14. Run a final status-sync check: ensure task status and session ID agree between `sprint.md` and the latest section in `progress.md`

## Key Rules
- Focus on one task only
- Always document in progress.md with session ID isolation
- Always include Sprint-ID and Task-ID in each progress session to prevent cross-sprint ambiguity
- **Log token metrics** with each session for resource tracking
- Validate with CI/CD before marking DONE
- Never leave tasks as DOING when ending
- Document blockers; proceed with available resources
- Execute autonomously; never ask permission
- Preserve traceability to the original `sprint.md` requirement set
- Do not treat added implementation tasks as proof that the original requirement was satisfied
- Call out repeated gate failures as process issues, not just one-off remediation notes
