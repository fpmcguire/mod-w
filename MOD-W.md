# Moderated AI Development Workflow (MOD-W)

MOD-W is a role-driven, document-centered workflow for AI-assisted software development. It separates product, design, technical, implementation, review, and verification decisions across distinct roles, enforces cross-validation between multiple AI agents and models, and requires a human Moderator to approve every step before it is accepted.

Full methodology reference: https://github.com/fpmcguire/mod-w

---

## Roles

| Role | Owns | AI agent (default) |
| ---- | ---- | ------------------ |
| **Moderator** | Workflow orchestration, go/no-go authority, HITL gate | Human only |
| **Product Owner** | What and why - `PRODUCT.md`, acceptance intent | Claude chatbot + Perplexity + Gemini (Definition); Claude Code SubAgent (Validation) |
| **Designer + Prototyper** | Approved visual behavior, interaction intent, prototype evidence, advisory architecture notes | Claude Design |
| **Tech Lead** | How - `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, `ROADMAP.md`, `STEP-XX.md`, technical review | Codex (reads `AGENTS.md` at repo root) |
| **Development Team** | Implementation - code, tests, docs for each Step | Claude Code (default) or Claude Design (visual Steps) |
| **QA / Tester** | End-to-end verification - `QA.md` | Claude Code SubAgent |

The Moderator is always human. Tech Lead is Codex. Architecture is authored by Codex, never by Claude Design.

---

## Workflow Summary

1. **Product Definition** - Product Owner produces approved `PRODUCT.md`.
2. **Prototype Ceremony (optional)** - Designer + Prototyper produces `DESIGN-SPEC.md`, `prototype/`, and `ARCHITECTURE-NOTES.md` when visual or interaction risk warrants it.
3. **Architecture Handoff (mandatory if prototype ran)** - Codex consumes `PRODUCT.md`, bounded `DESIGN-SPEC.md`, complete prototype inventory, and evidence-based `ARCHITECTURE-NOTES.md`; then authors `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, `ROADMAP.md`, `CLAUDE.md`, `AGENTS.md`, and the first `STEP-XX.md`.
4. **Step Definition** - Codex writes `STEP-XX.md` with requirements, relevant Design IDs, Reference Implementation disposition, and assumption disposition when Claude Design implements from its own prototype.
5. **Implementation Options Gate** - Development Team proposes a plan and waits for Moderator approval.
6. **Implementation** - Development Team implements only the approved Step and runs the blocking build gate.
7. **Tech Lead Review** - Codex reviews and writes `REVIEW.md` before QA acceptance.
8. **QA + Product Owner Validation** - QA writes `QA.md`; Product Owner validates acceptance intent.
9. **Moderator Final Gate** - Moderator approves, tags, and advances `ROADMAP.md`.

---

## Design and Prototype Authority

`DESIGN-SPEC.md` becomes authoritative only after Product Owner and Moderator approval, and only for user-facing visual behavior, interaction intent, screen composition, component states and variants, accessibility expectations, and approved user-facing terminology and content presentation.

It is not independently authoritative for production file paths, service or module boundaries, framework or library choices, canonical domain types, internal implementation names, test implementation strategy, or technical component decomposition. Those matters remain under Tech Lead authority.

`prototype/` is a research artifact. `ARCHITECTURE-NOTES.md` is advisory evidence. Prototype artifacts do not silently become production architecture.

---

## Canonical Documents

All MOD-W docs live under `mod-w/` in the project except root-level tool configs. `CLAUDE.md` and `AGENTS.md` live at the repo root. The optional `prototype/` folder also lives at the repo root.

`DESIGN-SPEC.md` is the canonical MOD-W design artifact. Optional `DESIGN.md` is broader project documentation for reusable design-system foundations, brand language, or durable visual principles.

---

## Backfill and Gates

Backfill produces reference documentation or evidence from work that already exists. A re-executed gate runs the current ceremony again and produces new authoritative outputs under the present workflow. Retroactive approval declares historical work compliant without rerunning the required gate; it is prohibited.

Existing work may be analyzed and backfilled, but it may not be retroactively declared compliant. Authoritative adoption requires the applicable gate to be re-executed.

---

## Operating Rules

- Single-role-per-session remains enforced.
- The same model does not both author a Step and implement that Step.
- Every Step receives Codex Tech Lead review before QA acceptance.
- Every Step receives Moderator final approval before tagging and Roadmap advancement.
- `ARCHITECTURE-NOTES.md` remains advisory.
- `Adopt as-is` never bypasses architecture, review, QA, tests, accessibility, security, or production-quality requirements.

---

MOD-W v4.0.1 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
