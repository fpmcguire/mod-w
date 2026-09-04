# AI Agents

**Project:** {{PROJECT_NAME}}
**Date:** {{DATE}}
**Owner:** {{TECH_LEAD_NAME}}

---

## Overview

This project uses multiple AI agents under MOD-W. Each agent has a defined role, controlled scope, and human moderation.

---

## Agents

### Product Owner

**Role:** Product definition and acceptance validation
**Interfaces:** Claude chatbot + Perplexity + Gemini for definition; Claude Code SubAgent for validation

Responsibilities:

- Author and maintain `product.md`.
- Validate completed Steps against acceptance intent after Tech Lead approval.

### Designer + Prototyper

**Role:** Optional design and prototype role
**Interface:** Claude Design

Responsibilities:

- Produce `design-spec.md` with bounded authority, Design IDs, traceability, and approval record.
- Produce `prototype/` with inventory.
- Produce advisory `architecture-notes.md` with evidence and confidence.

Constraints:

- Does not author architecture, Steps, review, QA, or production code except when separately assigned as Development Team for an approved Step.
- Prototype artifacts do not silently become production architecture.

### Tech Lead

**Role:** Architecture, planning, Step authoring, and technical review
**Interface:** Codex

Responsibilities:

- Author and maintain `architecture.md`, `domain-language.md`, `roadmap.md`, `step-xx.md`, `CLAUDE.md`, `AGENTS.md`, and `cross-validation.md`.
- Create or update minimal root tool config when project setup changes.
- Perform Architecture Handoff when Prototype Ceremony ran.
- Review completed Steps and write `review.md` before QA acceptance.

### Development Team

**Role:** Implementation
**Interface:** Claude Code by default; Claude Design only by Moderator assignment in `step-xx.md`

Responsibilities:

- Implement the approved `step-xx.md`.
- Preserve relevant Design ID intent.
- Run the blocking build gate.
- Apply normal production adaptation for any Reference Implementation.

### QA

**Role:** Acceptance validation
**Interface:** Claude Code SubAgent

Responsibilities:

- Validate implementation against `step-xx.md` acceptance checks.
- Verify approved Design ID intent where applicable without treating prototype code as authoritative.
- Write `qa.md`.

---

## Agent Interaction Rules

- Moderator is always human.
- No agent self-approves its work.
- Planning and implementation are separated.
- The same model does not both author and implement a Step.
- `architecture.md` is authored by Codex, never Claude Design.
- Every Step receives Codex Tech Lead review before QA acceptance.
- Every Step receives Moderator final approval before tagging and Roadmap advancement.
- Single-role-per-session remains enforced.
- Historical work cannot receive retroactive approval.

---

MOD-W v5.0.0
