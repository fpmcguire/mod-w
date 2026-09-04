# Quality Gates

Quality gates are explicit, non-negotiable checkpoints that AI-generated artifacts must pass before they are accepted. Gates are defined per Step in `step-xx.md`, evaluated by the Codex Tech Lead in `review.md`, verified by QA in `qa.md`, and accepted by the human Moderator at the final gate.

---

## Gate Levels

### Level 1 - Baseline

Every Step must pass these criteria:

- [ ] Output matches the scope defined in `step-xx.md`.
- [ ] Output uses domain language terms correctly per `domain-language.md`.
- [ ] Output preserves approved Design ID intent where applicable per `design-spec.md`.
- [ ] No hallucinated facts, APIs, libraries, or references.
- [ ] No placeholders, TODOs, or stub implementations left unresolved.
- [ ] No real credentials, personal data, or sensitive information included.

### Level 2 - Code Quality

In addition to Level 1:

- [ ] Code follows project patterns and conventions per `architecture.md`.
- [ ] Names align with `domain-language.md`.
- [ ] Error handling is present and appropriate.
- [ ] No obvious security vulnerabilities.
- [ ] Code is testable.

### Level 3 - Completeness

In addition to Levels 1 and 2:

- [ ] All acceptance criteria from `step-xx.md` are met.
- [ ] Tests are present and pass.
- [ ] Integration with existing code does not break existing tests.
- [ ] Documentation is updated if public interfaces changed.

---

## Applying Gates

1. The Tech Lead specifies the gate level in `step-xx.md`.
2. The Tech Lead evaluates technical criteria in `review.md`.
3. QA verifies behavior and evidence in `qa.md` after Tech Lead approval.
4. The Moderator evaluates the complete review and verification record at the final gate.
5. A Step may only be accepted if all criteria are met.

---

## Gate Waiver Policy

Quality gates may not be waived. If a gate criterion cannot be met, the team must return the Step to In Progress, revise acceptance criteria with Product Owner approval, or split the Step into smaller Steps.

---

MOD-W v5 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
