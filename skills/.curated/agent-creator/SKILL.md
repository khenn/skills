---
name: agent-creator
description: Create and maintain Codex sub-agent profiles (roles, personas, and guardrails) with consistent config, validation, and one-line request handling.
---

# Skill: Agent Creator

## Purpose
Create, update, and validate Codex multi-agent role profiles so teams can reliably run specialist agents with clear scope, behavior, and safety constraints.

## Use This Skill When
- The user asks to add or update a sub-agent role/persona in Codex.
- The user asks to standardize agent configs across projects or global scope.
- The user gives a short request (for example: "create artist agents") and expects end-to-end role generation.

## Inputs Required
- Target scope: project-local (`.codex/`) or global (`~/.codex/`).
- Requested role type(s) and persona intent.
- Constraints: allowed/forbidden actions, read/write scope, mutation policy.
- Runtime preferences (model, reasoning effort, sandbox intent).

## Outputs Produced
- `config.toml` role registration entries.
- Role config files (for example `agents/<role>.toml`).
- Role instruction content (`developer_instructions` or linked docs).
- Validation report (parse check + smoke test) and assumptions log.

## Safety and Privacy
- Do not include secrets, credentials, API keys, or private user data in role instructions.
- Keep role permissions least-privilege (explicit write scope, mutation constraints).
- Require explicit user approval before destructive or public-sharing behavior.
- Prefer output-only mode for newly created roles until pilot quality is confirmed.

## One-Line Request Behavior (Required)
When prompts are underspecified, proceed with defaults and assumptions unless ambiguity is high-risk.

Required sequence:
1. Infer missing fields from context.
2. Apply role template defaults.
3. Generate role config + instructions.
4. Validate parse.
5. Run spawn smoke test.
6. Return created files + assumptions + test results.

## Required Role Contract Sections
Every created role must explicitly define:
- Purpose and responsibilities
- Operations contract (allowed/forbidden actions)
- Read/write scope
- Mutation policy
- Delegation policy
- Quality gates
- Handoff schema (`Findings`, `Required changes`, `Optional improvements`, `Go/No-Go`)

## Read Additional References Only As Needed
- Read `references/workflows.md` for setup/update pipeline and validation.
- Read `references/artist-role-template.md` for the reusable artist template.
