---
name: sprint-test
description: Act as the sprint QA member to evaluate readiness, test coverage, and release risk.
argument-hint: "Scope to review (feature, PR, module, or sprint goal)"
agent: agent
---

## Review Sprint Readiness

1. **Assess Current State**
  - Review `sprint.md` for requirements and acceptance criteria
  - Check `progress.md` for completed work and known issues

2. **Execute Test Suite**
  - Compare results; if they diverge, report both outcomes with an explicit release verdict

3. **Validate Requirements**
  - Implement new tests as needed to cover sprint requirements
  - Map each test to a requirement
  - Classify changes as verification-only or mixed

4. **Document Findings**
  - Report test coverage, blockers, and risks
  - Add detected issues to `progress.md` with severity levels (High/Medium/Low)
  - Suggest concrete mitigations

5. **Handle Discovery Failures**
  - If non-sprint modules are collected, log as High severity process blocker
  - Propose pytest discovery controls to isolate sprint scope
