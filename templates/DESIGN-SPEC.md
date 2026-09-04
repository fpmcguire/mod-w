# Design Spec - {{PROJECT_NAME}}

**Date:** {{DATE}}
**Designer:** {{DESIGNER_NAME}}
**Authored in:** {{CLAUDE_DESIGN | CLAUDE_CHATBOT | GEMINI}}
**Prototype:** {{PROTOTYPE_PATH or "n/a"}}

---

## Authority Boundary

After Product Owner and Moderator approval, this spec is authoritative for user-facing visual behavior, interaction intent, screen composition, component states and variants, accessibility expectations, and approved user-facing terminology and content presentation.

It is not independently authoritative for production file paths, service or module boundaries, framework or library choices, canonical domain types, internal implementation names, test implementation strategy, or technical component decomposition. Those decisions remain under Tech Lead authority in `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, and `STEP-XX.md`.

The prototype is evidence for this spec, not an authoritative production source.

---

## Approval Record

### Product Owner review

- **Status:** Pending / Approved / Changes requested
- **Reviewer:**
- **Date:**
- **Conditions or findings:**

### Tech Lead feasibility pre-review

- **Status:** Pending / Reviewed
- **Reviewer:**
- **Date:**
- **Feasibility concerns:**
- **Architecture questions:**

### Moderator gate

- **Status:** Pending / Approved for Architecture Handoff / Rejected
- **Moderator:**
- **Date:**
- **Conditions:**

Product Owner and Moderator approval are required before this spec becomes authoritative within its boundary. Tech Lead pre-review is advisory and does not transfer architecture authority. Approval of this spec does not make the prototype authoritative.

---

## DESIGN.md Policy

`DESIGN-SPEC.md` is the canonical MOD-W design artifact. A separate `DESIGN.md` is optional project documentation for broader design-system foundations, brand language, or durable visual principles.

When both exist, `DESIGN.md` contains reusable principles and global design-system guidance; `DESIGN-SPEC.md` contains product-specific screens, components, states, interactions, traceability, and approval. Reference `DESIGN.md` instead of duplicating token catalogues here.

---

## Design Principles

- Clear
- Consistent
- Minimal
- Accessible

---

## 1. Visual Identity

### 1.1 Color Palette

### 1.2 Typography

### 1.3 Spacing & Layout System

### 1.4 Borders, Radius & Elevation

### 1.5 Tone & Personality

---

## 2. Accessibility Baseline

- WCAG AA compliance
- Keyboard navigation required
- Visible focus states

---

## 3. Component Library

> One section per component. For each component document: name (from `DOMAIN_LANGUAGE.md`), one-sentence purpose, states (default / hover / active / disabled / loading / empty / error), variants, and `data-testid` convention.

### 3.x {{COMPONENT_NAME}}

- **Purpose:**
- **States:**
- **Variants:**
- **data-testid:** `{{feature}}-{{component}}-{{element}}-{{modifier?}}`

---

## 4. Screen Layouts

> One section per screen. Document layout structure, components present and their positions, empty / loading / error states, and responsive behaviour (if in scope).

### 4.x {{SCREEN_NAME}}

---

## 5. Interaction Patterns

- Selection / hover / focus
- Keyboard navigation
- Transitions

---

## 6. Design Traceability

> Assign stable IDs such as `DS-001`. Every in-scope screen, major component, or significant interaction must map to at least one Product requirement. `First implementation Step` may be `TBD` during kickoff. Prototype evidence may be a file, page, route, screenshot, or flow. A Roadmap is not required before design work begins.

| Design ID | Design element | Product requirement | Prototype evidence | First implementation Step | Notes |
| --------- | -------------- | ------------------- | ------------------ | ------------------------- | ----- |
| DS-001    |                | R-001               |                    | TBD                       |       |

---

## 7. Domain Language Proposals  *(v4)*

> Terms the prototype surfaced that are NOT in `DOMAIN_LANGUAGE.md`. Each entry is a proposal for the Tech Lead to ratify, modify, or reject during Architecture Definition. Do not treat any term here as canonical.

| Proposed term | Form (type / value / both) | Definition | Rationale | First appearance |
| ------------- | -------------------------- | ---------- | --------- | ---------------- |
|               |                            |            |           |                  |

If no terms proposed, state "None proposed."

---

## 8. Scope Rules

- Only define components required for current or near-term Steps
- Do not design beyond approved PRODUCT scope
- Each in-scope screen, major component, and significant interaction must have a Design ID and Product requirement mapping
- When `ROADMAP.md` exists, connect Design IDs to the first implementation Step

---

## 9. UI Scope Rules

- Only implement UI elements in current `STEP-XX.md`
- Future states must not be implemented early
- Design supports incremental delivery

---

## 10. Open Questions

| Question | Owner | Status |
| -------- | ----- | ------ |

---

MOD-W v4.0.1
