# Moderator - Frontend Saved Views Prompt

> Use this prompt as the human Moderator's operating checklist for the Frontend Saved Views example.
> The Moderator is not an implementation agent; this role controls scope, context, approvals, and final acceptance.

---

## Role

You are the Moderator for the Frontend Saved Views example in the Moderated AI Development Workflow.

Your job is to orchestrate the handoffs between roles, decide when outputs are approved, and keep the workflow honest. You do not delegate final authority to any AI agent.

---

## Source of Truth

Use these in order:

1. Current Moderator decision
2. `mod-w/MOD-W.md`
3. `mod-w/product.md`
4. approved `mod-w/design-spec.md`, if present
5. `mod-w/architecture.md`
6. `mod-w/domain-language.md`
7. active `mod-w/step-xx.md`
8. `mod-w/review.md`, `mod-w/qa.md`, and `mod-w/validation/`

---

## Responsibilities

- Assign one role per session and keep each role in its lane.
- Approve or reject `mod-w/product.md`, `mod-w/architecture.md`, `mod-w/roadmap.md`, and each `mod-w/step-xx.md`.
- Confirm the Development Team plan before implementation begins.
- Ensure review, QA, and Product Owner validation complete before final acceptance.
- Resolve disagreements logged in `mod-w/validation/discrepancies.md`.
- Create the final Step acceptance record and annotated tag when a Step is complete.

---

## Constraints

- Do not allow retroactive approval of historical work.
- Do not let one agent both author and implement the same Step.
- Do not let any agent resolve Claude/Codex disagreements without human direction.
- Do not accept a Step until build/test evidence and QA evidence are present or explicitly waived.

---

## Operating Loop

1. Identify the active Step and role.
2. Provide only the context that role needs.
3. Ask the role to restate scope and risks.
4. Approve the plan or request changes.
5. Review the output against the active artifact.
6. Route rework, validation, or acceptance.

---

MOD-W v5 example - Frontend Saved Views
