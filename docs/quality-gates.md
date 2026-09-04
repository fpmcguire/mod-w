# Quality Gates

Quality gates are explicit, non-negotiable checkpoints that AI-generated artifacts must pass before they are accepted. Gates are defined per Step in `STEP-XX.md`, evaluated by the Codex Tech Lead in `REVIEW.md`, verified by QA in `QA.md`, and accepted by the human Moderator at the final gate.

---

## Gate Levels

### Level 1 - Baseline

Every Step must pass these criteria:

- [ ] Output matches the scope defined in `STEP-XX.md`.
- [ ] Output uses domain language terms correctly per `DOMAIN_LANGUAGE.md`.
- [ ] Output preserves approved Design ID intent where applicable per `DESIGN-SPEC.md`.
- [ ] No hallucinated facts, APIs, libraries, or references.
- [ ] No placeholders, TODOs, or stub implementations left unresolved.
- [ ] No real credentials, personal data, or sensitive information included.

### Level 2 - Code Quality

In addition to Level 1:

- [ ] Code follows project patterns and conventions per `ARCHITECTURE.md`.
- [ ] Names align with `DOMAIN_LANGUAGE.md`.
- [ ] Error handling is present and appropriate.
- [ ] No obvious security vulnerabilities.
- [ ] Code is testable.

### Level 3 - Completeness

In addition to Levels 1 and 2:

- [ ] All acceptance criteria from `STEP-XX.md` are met.
- [ ] Tests are present and pass.
- [ ] Integration with existing code does not break existing tests.
- [ ] Documentation is updated if public interfaces changed.

---

## Applying Gates

1. The Tech Lead specifies the gate level in `STEP-XX.md`.
2. The Tech Lead evaluates technical criteria in `REVIEW.md`.
3. QA verifies behavior and evidence in `QA.md` after Tech Lead approval.
4. The Moderator evaluates the complete review and verification record at the final gate.
5. A Step may only be accepted if all criteria are met.

---

## Gate Waiver Policy

Quality gates may not be waived. If a gate criterion cannot be met, the team must return the Step to In Progress, revise acceptance criteria with Product Owner approval, or split the Step into smaller Steps.

---

MOD-W v4.0.1 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
