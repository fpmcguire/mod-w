# AI Agents

**Project:** Frontend Saved Views
**Owner:** Tech Lead

## Overview

This example uses multiple AI agents under MOD-W. Each agent has a defined role, controlled scope, and human moderation.

## Agents

### Product Owner

Defines product intent and validates completed work against `product.md`.

### Tech Lead

Owns `architecture.md`, `domain-language.md`, `roadmap.md`, step briefs, and technical review.

### Development Team

Implements only the approved `step-01.md` scope.

### QA

Validates accepted implementation against the step acceptance checks and records evidence in `qa.md`.

## Agent Interaction Rules

- Moderator is always human.
- No agent self-approves its work.
- Planning and implementation are separated.
- Conflicting Claude/Codex conclusions are logged in `validation/discrepancies.md`.
