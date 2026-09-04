# Step Lifecycle

Every meaningful change is delivered as a Step: small enough to implement, review, and verify end to end without overloading any agent or the Moderator.

This lifecycle assumes the default v4 roles:

- Moderator: human
- Product Owner: definition role and validation SubAgent
- Designer + Prototyper: optional during Project Kickoff
- Tech Lead: Codex
- Development Team: Claude Code by default; Claude Design only by Step assignment
- QA: Claude Code SubAgent

---

## 1. Define the Step

**Who:** Tech Lead (Codex), Moderator
**Artifacts:** `PRODUCT.md`, `DESIGN-SPEC.md` if present, `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, `ROADMAP.md`, `STEP-XX.md`

- Tech Lead reads the approved source artifacts.
- If `DESIGN-SPEC.md` exists, Tech Lead cites relevant Design IDs in `STEP-XX.md`.
- If prototype inputs influenced the Step, Tech Lead records Reference Implementation disposition in `STEP-XX.md`.
- If Claude Design will implement a Step derived from its own prototype, Tech Lead records accepted, modified, rejected, and mandatory-divergence prototype assumptions.
- Moderator approves the Step before implementation begins.

Output: Approved `STEP-XX.md`.

---

## 2. Brief the Development Team

**Who:** Moderator -> assigned Development Team interface
**Artifacts:** `CLAUDE.md`, `AGENTS.md`, active `STEP-XX.md`

- Confirm `CLAUDE.md` and `AGENTS.md` are current at the repo root.
- Start the assigned interface from `STEP-XX.md`.
- State the active Step file path.
- If Claude Design is assigned, confirm it did not author the Step.
- If the Step derives from Claude Design's own prototype, confirm the assumption-disposition section is present.

Output: Shared understanding of the Step.

---

## 3. Implementation Options Gate

**Who:** Development Team -> Moderator
**Artifacts:** `STEP-XX.md`, `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, `DESIGN-SPEC.md` if relevant

- Development Team reads relevant files and proposes a plan.
- No files are written before Moderator approval.
- Moderator may request options or ramifications.

Output: Moderator-approved implementation plan.

---

## 4. Implement the Step

**Who:** Development Team
**Artifacts:** Code, tests, docs

- Implement only the approved scope.
- Treat `STEP-XX.md`, `ARCHITECTURE.md`, and `DOMAIN_LANGUAGE.md` as controlling.
- Preserve approved Design ID intent where applicable.
- Do not treat prototype code as authoritative.
- Run the blocking build gate (`{{BUILD_COMMAND}}` and `{{TEST_COMMAND}}`) until clean.

Output: Implemented Step with passing build gate.

---

## 5. Tech Lead Review and Revision Loop

**Who:** Tech Lead (Codex) <-> Development Team
**Artifacts:** `REVIEW.md`

- Tech Lead reads `STEP-XX.md`, implementation diff, relevant architecture, and relevant design IDs.
- Tech Lead reviews architecture, maintainability, scope, domain language, tests, and design-intent alignment.
- Tech Lead writes `REVIEW.md`.
- Development Team addresses must-fix findings and reruns the build gate.
- Loop continues until Tech Lead approves.

Output: `REVIEW.md` with Tech Lead approval.

---

## 6. QA and Product Owner Validation

**Who:** QA SubAgent, Product Owner SubAgent
**Artifacts:** `QA.md`, Product Owner sign-off

Triggered only after Tech Lead approval.

- QA validates implementation files and `STEP-XX.md` acceptance checks.
- QA verifies approved Design ID intent where applicable without treating prototype code as authoritative.
- Product Owner validates acceptance intent against `PRODUCT.md`.

Output: `QA.md` and Product Owner sign-off.

---

## 7. Moderator Spot Check

**Who:** Moderator
**Artifacts:** `QA.md`, Product Owner sign-off, Workbench

- Moderator reviews `REVIEW.md`, `QA.md`, and Product Owner sign-off.
- Moderator performs manual checks flagged by QA.
- Substantial issues return to the Development Team.

Output: Step cleared or returned for focused revision.

---

## 8. Tag and Advance

**Who:** Moderator
**Artifacts:** Git history, annotated tag, `ROADMAP.md`

- Moderator confirms every required gate passed.
- Moderator creates an annotated Git tag for the Step.
- Moderator advances `ROADMAP.md`.

Output: Traceable milestone and next Step selection.

---

## 9. Documentation Update

**Who:** Moderator, with the owning role for affected artifacts
**Artifacts:** `PRODUCT.md`, `DESIGN-SPEC.md`, `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, `ROADMAP.md`

Update planning artifacts when accepted work changes behavior, visual intent, architecture, terms, or future sequencing.

---

## Completion Definition

A Step is complete only when:

- `STEP-XX.md` is satisfied.
- Code builds cleanly in the Workbench.
- Relevant tests pass or documented exceptions are approved.
- Behavior matches acceptance checks.
- Relevant Design IDs are satisfied where applicable.
- Tech Lead has approved in `REVIEW.md`.
- QA has updated `QA.md`.
- Moderator has given final approval.
- An annotated Git tag has been created.

---

MOD-W v4.0.1 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
