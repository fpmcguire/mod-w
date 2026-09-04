# Ceremonies in Moderated AI Development Workflow

Ceremonies are structured, Moderator-gated events that create shared understanding and traceable decisions.

---

## 1. Project Kickoff

The kickoff has up to three sequential phases. No phase ends until the Moderator explicitly approves its output.

### 1a. Product Definition

**When:** Once at project start; revisited when scope changes materially
**Who:** Moderator, Product Owner, research and cross-validation tools

**Purpose:** Produce a Moderator-approved `PRODUCT.md`.

**Output:** Approved `PRODUCT.md`.

### 1b. Prototype Ceremony (optional, v4)

**When:** After `PRODUCT.md` is approved, when visual or interaction risk warrants it
**Who:** Moderator, Designer + Prototyper (Claude Design)

Produces `DESIGN-SPEC.md`, `prototype/`, and `ARCHITECTURE-NOTES.md`.

`DESIGN-SPEC.md` becomes authoritative only after Product Owner and Moderator approval, and only within its bounded visual and interaction authority. The prototype remains non-authoritative. `ARCHITECTURE-NOTES.md` remains advisory.

**Output:** Approved `DESIGN-SPEC.md`, complete `prototype/` inventory, advisory `ARCHITECTURE-NOTES.md`.

See `docs/prototype-ceremony.md`.

### 1c. Architecture Definition / Architecture Handoff

**When:** After `PRODUCT.md` approval; after Prototype Ceremony if it ran
**Who:** Moderator, Tech Lead (Codex)

**Purpose:** Produce approved technical artifacts before Roadmap and Step implementation.

If the Prototype Ceremony ran, this is the Architecture Handoff: Codex consumes `PRODUCT.md`, bounded `DESIGN-SPEC.md`, the complete `prototype/` inventory, and `ARCHITECTURE-NOTES.md`; evaluates evidence; and independently authors `ARCHITECTURE.md`.

**Output:** Approved `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, `ROADMAP.md`, `CLAUDE.md`, `AGENTS.md`, and first `STEP-XX.md`.

See `docs/architecture-handoff.md`.

---

## 2. Step Planning

**When:** Before each Step begins
**Who:** Tech Lead (Codex), Moderator, Product Owner when needed

**Purpose:** Define scope, inputs, outputs, quality gate, relevant Design IDs, and implementation constraints for the next Step.

**Activities:**

- Author or refine `STEP-XX.md`.
- Confirm acceptance criteria with Product Owner.
- Cite relevant Design IDs when `DESIGN-SPEC.md` exists.
- Record Reference Implementation disposition when candidate prototype code exists.
- If Claude Design implements from its own prototype, record accepted, modified, rejected, and mandatory-divergence prototype assumptions.

**Output:** Approved `STEP-XX.md`.

---

## 3. Implementation Options Gate

**When:** After Step approval, before code is written
**Who:** Moderator and assigned Development Team interface

**Purpose:** Confirm implementation plan before file edits.

**Output:** Moderator-approved implementation plan.

---

## 4. Development Team Session

**When:** During the Step after the Options Gate
**Who:** Moderator and Development Team

**Purpose:** Implement the approved Step directly in the repository.

**Activities:**

- Development Team implements only the approved `STEP-XX.md`.
- Development Team treats `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, and `STEP-XX.md` as controlling.
- If Claude Design implements from its own prototype, it follows the assumption disposition in `STEP-XX.md`.
- Development Team runs the blocking build gate.

**Output:** Implemented Step with passing build gate.

---

## 5. Tech Lead Review

**When:** After Development Team handoff and before QA acceptance
**Who:** Tech Lead (Codex)

**Purpose:** Review implementation for architecture, maintainability, scope compliance, domain language, tests, and approved design intent.

**Output:** `REVIEW.md` with Tech Lead verdict and findings.

---

## 6. QA and Product Owner Validation

**When:** After Tech Lead approval
**Who:** QA SubAgent and Product Owner SubAgent

**Purpose:** Verify behavior against acceptance checks and product intent.

QA may verify approved Design ID intent but does not treat prototype code as authoritative.

**Output:** `QA.md` and Product Owner sign-off.

---

## 7. Moderator Final Gate

**When:** After Tech Lead review, QA, and Product Owner validation
**Who:** Moderator

**Purpose:** Human final approval before tagging and Roadmap advancement.

**Output:** Annotated Git tag and updated `ROADMAP.md`.

---

## Backfill and Retroactive Approval

Backfill produces reference documentation or evidence from work that already exists. A re-executed gate runs the current ceremony again and produces new authoritative outputs under the present workflow. Retroactive approval declares historical work compliant without rerunning the required gate and is prohibited.

Existing work may be analyzed and backfilled, but it may not be retroactively declared compliant. Authoritative adoption requires the applicable gate to be re-executed.

---

MOD-W v4.0.1 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
