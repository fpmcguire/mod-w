# Document Lifecycle

**Project:** {{PROJECT_NAME}}
**Owner:** Moderator
**Version:** MOD-W v4.0.1

---

## Purpose

This document defines ownership, creation, update timing, and forward flow for MOD-W documents.

---

## Core Principle

Documents evolve in controlled stages:

```text
PRODUCT -> DESIGN-SPEC (optional) -> ARCHITECTURE -> ROADMAP -> STEP-XX -> CODE -> REVIEW -> QA -> MODERATOR FINAL GATE
```

No document should be updated out of order without Moderator approval.

---

## Document Ownership Matrix

| Document | Owner | Role Responsibility |
| -------- | ----- | ------------------- |
| `PRODUCT.md` | Product Owner | Define intent and requirements |
| `DESIGN-SPEC.md` | Designer + Prototyper | Define bounded visual and interaction design |
| `DESIGN.md` (optional) | Designer / Moderator | Define durable design-system foundations |
| `ARCHITECTURE-NOTES.md` | Designer + Prototyper | Provide advisory prototype observations |
| `ARCHITECTURE.md` | Tech Lead (Codex) | Define technical architecture |
| `DOMAIN_LANGUAGE.md` | Tech Lead | Define canonical terminology |
| `ROADMAP.md` | Tech Lead | Define execution plan |
| `STEP-XX.md` | Tech Lead | Define scoped work |
| `REVIEW.md` | Tech Lead | Record technical review |
| `QA.md` | QA / Tester | Validate behavior |
| `AI_AGENTS.md` | Tech Lead | Define agent setup |
| `CLAUDE.md` | Tech Lead | Configure Development Team |
| `AGENTS.md` | Tech Lead | Configure Codex Tech Lead |

---

## Traceability Model

```text
R-ID -> DS-ID -> D-ID -> STEP-XX -> CODE -> REVIEW -> QA
```

Design IDs may be `TBD` for first implementation Step during kickoff, but every in-scope screen, major component, or significant interaction must map to at least one Product requirement.

---

## Backfill Rules

Backfill produces reference documentation or evidence from work that already exists. A re-executed gate runs the current ceremony again and produces new authoritative outputs under the present workflow. Retroactive approval declares historical work compliant without rerunning the required gate and is prohibited.

Existing work may be analyzed and backfilled, but it may not be retroactively declared compliant. Authoritative adoption requires the applicable gate to be re-executed.

---

## Active Context Rule

At any moment, only one `STEP-XX.md` is active. Agents must focus on that Step and ignore unrelated scope.

---

MOD-W v4.0.1 - Document Lifecycle
