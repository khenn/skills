---
name: skill-governance
description: Create, refactor, and validate repository skills using policy-driven, minimal-context best practices with deterministic checks.
---

# Skill: Skill Governance

## Purpose
Use this skill to create or refactor skills with consistent structure, strict validation gates, and minimal-context loading behavior.

## Use This Skill When
- You need to create a new skill scaffold.
- You need to refactor skills for tighter scope and reduced context loading.
- You need to validate skill packages, trigger behavior, or fixture conformance.
- You need to add CI checks for skill quality gates.

## Inputs Required
- Target repository root.
- Skills root path (default: `skills/`).
- Skill name (for scaffold operations).

## Outputs Produced
- Policy-compliant skill package(s).
- Validation + trigger test results.
- Optional CI workflow for automated enforcement.

## Safety and Privacy
- Do not include secrets, user-local environment values, PII, or proprietary content in reusable skill assets.
- Prefer templates and generalized guidance over project-specific confidential details.

## Workflow
1. Use `scripts/create-skill-scaffold.ts` to create a compliant skeleton when starting a new skill.
2. Apply references/templates from `references/` to set policy/checklist/test/CI baseline.
3. Run deterministic checks:
   - `scripts/validate-skill-package.ts`
   - `scripts/test-skill-triggers.ts`
   - `scripts/test-skill-validator-fixtures.ts`
4. Record migration/testing outcomes in session notes.

## Read Additional References Only As Needed
- Read `references/policy-template.md` when authoring or normalizing skill policy.
- Read `references/review-checklist-template.md` when creating merge gates.
- Read `references/trigger-test-template.json` when adding prompt trigger fixtures.
- Read `references/ci-template-github-actions.md` for CI wiring.
- Read `references/migration-playbook.md` for phased migration from repo-local tooling to portable skill packaging.
