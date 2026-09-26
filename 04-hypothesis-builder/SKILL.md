---
name: Vercel Hypothesis Builder
description: Convert Vercel code observations and change signals into narrow, falsifiable security hypotheses with explicit controls and kill conditions.
---

# Vercel Hypothesis Builder

Use this skill whenever the team has observations but not yet a testable security claim.

## When To Use

- After Change Intelligence.
- After Source Trace reveals an ambiguous boundary.
- When multiple possible bug classes could explain one code path.
- Before writing a PoC.

## Good Hypothesis Properties

A good hypothesis states:

1. Who the attacker is.
2. What input they control.
3. Which guard should stop them.
4. Which security boundary may fail.
5. What observable effect would prove it.
6. What result would kill the hypothesis.

## Template

```text
ID:
TARGET:
VERSION:
ATTACKER:
PREREQUISITES:
INPUT:
ENTRYPOINT:
EXPECTED_GUARD:
SUSPECTED_FAILURE:
SINK:
SECURITY_BOUNDARY:
EXPECTED_IMPACT:
CONTROL:
NEGATIVE_CONTROL:
PROOF_REQUIRED:
KILL_CONDITION:
```

## Workflow

1. Remove vague language such as:
   - "might be vulnerable"
   - "possibly exploitable"
   - "looks dangerous"
2. Narrow the hypothesis to one boundary.
3. Choose harmless synthetic proof.
4. Define the baseline before the mutation.
5. Define one changed variable.
6. Define the negative control.
7. Define server-side or state-based evidence.
8. Define the exact kill condition.
9. Pass only testable hypotheses to reproduction.

## Examples of Strong Security Properties

- A team cannot access another team's resource by changing an identifier.
- A redirect allowlist is applied to every redirect hop.
- A sandbox cannot access a network destination prohibited by policy.
- A restored snapshot cannot inherit credentials or state from a different tenant.
- A path supplied by a package cannot escape its allowed root.
- A workflow cannot resume or mutate another workflow's state.

## Rules

- One hypothesis = one primary security property.
- Do not hide prerequisite complexity.
- Do not inflate potential impact before proof.
