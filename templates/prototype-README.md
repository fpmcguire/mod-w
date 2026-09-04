# Prototype - {{PROJECT_NAME}}

**Status:** Research artifact. **Non-authoritative.**

---

This folder contains a clickable prototype produced by the **Designer + Prototyper** role (Claude Design) during the Project Kickoff Prototype Ceremony.

## What this is

A working demonstration that the design works under realistic conditions. The prototype simulates the product's primary workflows, demonstrates every screen in `DESIGN-SPEC.md` scope, and exists as evidence the design is buildable.

## Prototype Inventory

### Screens or routes included

| Screen / route | Design IDs | Notes |
| -------------- | ---------- | ----- |
|                | DS-001     |       |

### States demonstrated

- Empty:
- Loading:
- Error:
- Disabled:
- Hover / focus / active:

### Simulated integrations

| Integration | Simulation approach | Files |
| ----------- | ------------------- | ----- |
|             |                     |       |

### Prototype-only controls

- ...

### Known limitations

- ...

### Explicitly out-of-scope behavior

- ...

### Architecturally relevant files

| File | Why it matters |
| ---- | -------------- |
| `prototype/...` | |

## What this is NOT

- **Not production code.** Do not import from this folder into `src/`.
- **Not architecturally canonical.** Patterns here are research output. The authoritative architecture lives in `mod-w/ARCHITECTURE.md`, authored by the Tech Lead.
- **Not a Reference Implementation by default.** A Reference Implementation status is granted only when the Tech Lead explicitly disposes of a specific prototype component in a `STEP-XX.md` section "Reference Implementation" block.

## How this folder is used downstream

1. The Tech Lead (Codex) inspects this folder during Architecture Definition as one of the kickoff inputs.
2. The Tech Lead must inspect the complete prototype inventory, run or view every in-scope flow, read all files listed as architecturally relevant, and sample supporting files as needed.
3. The Tech Lead may reference specific files here in `STEP-XX.md` as a Reference Implementation with one of three dispositions: `Adopt as-is`, `Adopt with modifications`, or `Reject`.
4. The Development Team reads dispositions in `STEP-XX.md` and proceeds accordingly. The Dev Team reads prototype files only when the approved Step names them as relevant.

## Lifecycle

- **Created:** During the Prototype Ceremony.
- **Frozen:** At the Architecture Handoff. Once `ARCHITECTURE.md` is approved, this folder is read-only except for explicitly approved backfill notes.
- **Retained:** For the life of the project, as historical context.

---

MOD-W v4.0.1
