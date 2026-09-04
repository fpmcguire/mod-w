# Review: Step {{STEP_NUMBER}}

**Project:** {{PROJECT_NAME}}
**Step:** {{STEP_NUMBER}} - {{STEP_TITLE}}
**Reviewer:** Tech Lead (Codex)
**Review Date:** {{DATE}}
**Development Team Interface:** {{CLAUDE_CODE | CLAUDE_DESIGN | OTHER}}

---

## Verdict

Pass / Pass with changes / Rework required

---

## Scope Check

- [ ] Output matches `step-xx.md` scope.
- [ ] Product requirements are satisfied.
- [ ] Relevant Design IDs are satisfied where applicable.
- [ ] Reference Implementation disposition was honored where applicable.
- [ ] Prototype code was not treated as authoritative production architecture.

---

## Requirement Coverage

| Requirement | Status      | Notes |
| ----------- | ----------- | ----- |
| R1          | Pass / Fail |       |

---

## Design ID Coverage _(if applicable)_

| Design ID | Status      | Notes |
| --------- | ----------- | ----- |
| DS-001    | Pass / Fail |       |

---

## Quality Gate Evaluation

### Level 1 - Baseline

- [ ] Domain language used correctly.
- [ ] No hallucinated APIs or libraries.
- [ ] No unresolved TODOs or placeholders.
- [ ] No sensitive data exposed.

### Level 2 - Code Quality

- [ ] Follows `architecture.md`.
- [ ] Naming matches `domain-language.md`.
- [ ] Error handling present.
- [ ] No obvious security issues.
- [ ] Code is testable.

### Level 3 - Completeness

- [ ] All acceptance checks met.
- [ ] Tests pass.
- [ ] No regressions identified.
- [ ] Documentation updated if needed.

---

## Findings

| #   | Finding | Severity                       | Related ID          | Resolution |
| --- | ------- | ------------------------------ | ------------------- | ---------- |
| 1   |         | Must fix now / Could fix later | R1 / DS-001 / D-001 |            |

---

## Moderator Final Gate Notes

> Moderator completes this after QA and Product Owner validation.

- **Status:** Pending / Approved / Rejected
- **Moderator:**
- **Date:**
- **Conditions:**

---

MOD-W v5.0.0
