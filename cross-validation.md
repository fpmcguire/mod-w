---
mode: parallel
last_set_by: moderator
last_set: 2026-09-04
---

# Cross-Validation Protocol

## Mode: parallel
Claude and Codex work independently. Neither reads the other's output until both have completed their pass for the current step. Each agent gathers context fresh from `product.md`, `architecture.md`, etc., not from anything the other wrote this session.

## Mode: sequential
Codex reads Claude's completed `review.md` for the current step, then validates against it. Claude's work is the baseline; Codex checks it.

## How to switch
Edit the `mode` field above. Each agent re-reads this file at the start of every validation pass; do not rely on a cached value from earlier in the session.

## Discrepancy handling
Regardless of mode, conflicting conclusions go in `validation/discrepancies.md`, not resolved automatically by either agent.
