# Document Lifecycle

**Project:** {{PROJECT_NAME}}
**Owner:** Moderator
**Version:** MOD-W v5

---

## Purpose

This document defines ownership, creation, update timing, and forward flow for MOD-W documents.

---

## Core Principle

Documents evolve in controlled stages:

```text
product.md -> design-spec.md (optional) -> architecture.md -> roadmap.md -> step-xx.md -> code -> review.md -> qa.md -> Moderator final gate
```

No document should be updated out of order without Moderator approval.

---

## Document Ownership Matrix

| Document | Owner | Role Responsibility |
| -------- | ----- | ------------------- |
| `product.md` | Product Owner | Define intent and requirements |
| `design-spec.md` | Designer + Prototyper | Define bounded visual and interaction design |
| `DESIGN.md` (optional) | Designer / Moderator | Define durable design-system foundations |
| `architecture-notes.md` | Designer + Prototyper | Provide advisory prototype observations |
| `architecture.md` | Tech Lead (Codex) | Define technical architecture |
| `domain-language.md` | Tech Lead | Define canonical terminology |
| `roadmap.md` | Tech Lead | Define execution plan |
| `step-xx.md` | Tech Lead | Define scoped work |
| `review.md` | Tech Lead | Record technical review |
| `qa.md` | QA / Tester | Validate behavior |
| `ai-agents.md` | Tech Lead | Define agent setup |
| `cross-validation.md` | Moderator | Define Claude/Codex validation mode |
| `agents/` | Tech Lead | Define tool-neutral roles |
| `rules/` | Tech Lead / Moderator | Define path-scoped constraints |
| `skills/` | Tech Lead / Moderator | Hold reusable MOD-W procedures |
| `validation/` | Moderator | Hold validation outputs and discrepancy logs |
| `CLAUDE.md` | Tech Lead | Configure Development Team |
| `AGENTS.md` | Tech Lead | Configure Codex Tech Lead |
| `.codex/config.toml` | Tech Lead / Moderator | Configure Codex project settings |
| `.claude/settings.json` | Tech Lead / Moderator | Configure Claude Code settings and hooks |
| `.mcp.json` | Tech Lead / Moderator | Configure shared MCP connections |

---

## Traceability Model

```text
R-ID -> DS-ID -> D-ID -> step-xx.md -> code -> review.md -> qa.md
```

Design IDs may be `TBD` for first implementation Step during kickoff, but every in-scope screen, major component, or significant interaction must map to at least one Product requirement.

---

## Backfill Rules

Backfill produces reference documentation or evidence from work that already exists. A re-executed gate runs the current ceremony again and produces new authoritative outputs under the present workflow. Retroactive approval declares historical work compliant without rerunning the required gate and is prohibited.

Existing work may be analyzed and backfilled, but it may not be retroactively declared compliant. Authoritative adoption requires the applicable gate to be re-executed.

---

## Active Context Rule

At any moment, only one `step-xx.md` is active. Agents must focus on that Step and ignore unrelated scope.

---

MOD-W v5 - Document Lifecycle
