---
name: Vercel Scope Guard
description: Verify Vercel program scope, target classification, environment ownership, and allowed testing mode before any research or validation begins.
---

# Vercel Scope Guard

Use this skill before any Vercel research cycle, whenever a target changes, or before moving from local source review to live validation.

## When To Use

- At the beginning of every hypothesis.
- Before testing any Vercel Platform asset.
- Before switching between VERCEL OSS and VERCEL PLATFORM.
- When a repository, feature, deployment, host, team, project, account, or third-party application is involved.
- When the Research Director is unsure whether a planned action is allowed.

## Core Rules

- VERCEL OSS defaults to LOCAL_ONLY testing against public source and locally controlled fixtures.
- VERCEL PLATFORM testing is OWNED_ACCOUNT_ONLY.
- Use only researcher-owned accounts, teams, projects, deployments, resources, and synthetic data.
- Never test third-party customer applications or data.
- Never treat a public endpoint as automatically in scope.
- Stop if scope, ownership, authorization, or environment classification is unclear.

## Workflow

1. Identify the active research lane:
   - `vercel-open-source`
   - `vercel-platform`

2. Record:
   - Program
   - Asset/repository
   - Exact version or deployment
   - Environment
   - Ownership
   - Intended action
   - Expected impact class

3. For OSS:
   - Confirm the repository is Vercel-owned and in the active program configuration.
   - Prefer stable release reproduction.
   - Keep testing local unless the program explicitly requires otherwise.

4. For Platform:
   - Confirm all accounts, projects, teams, resources, deployments, and test data are researcher-owned.
   - Use synthetic markers only.
   - Do not interact with unrelated tenants.

5. Classify the planned action:
   - ALLOWED
   - LOCAL_ONLY
   - OWNED_ACCOUNT_ONLY
   - NEEDS_SCOPE_REVIEW
   - OUT_OF_SCOPE

6. If not clearly ALLOWED, LOCAL_ONLY, or OWNED_ACCOUNT_ONLY, stop the workflow.

## Output

Return exactly:

```text
PROGRAM:
LANE:
TARGET:
VERSION/DEPLOYMENT:
ENVIRONMENT:
OWNERSHIP:
ACTION:
CLASSIFICATION:
SCOPE_EVIDENCE:
BLOCKERS:
VERDICT:
```

`VERDICT` must be one of:

- PROCEED
- HOLD
- STOP

## Fail-Closed Rules

- Unknown ownership -> HOLD.
- Third-party customer target -> STOP.
- Missing program classification -> HOLD.
- Live testing proposed for an OSS-local hypothesis without a need -> HOLD.
- Real secrets or unrelated user data required -> STOP.
