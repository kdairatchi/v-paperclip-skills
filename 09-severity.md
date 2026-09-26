---
name: Vercel Severity Review
description: Assess a confirmed Vercel vulnerability using proven prerequisites, boundary crossed, confidentiality/integrity/availability impact, and defensible CVSS reasoning.
---

# Vercel Severity Review

Use this skill only after Evidence Gate returns CONFIRMED.

## When To Use

- Before report-ready status.
- When impact or prerequisites are disputed.
- When selecting a HackerOne severity.

## Workflow

1. Record attacker prerequisites:
   - unauthenticated
   - authenticated
   - project member
   - team member
   - repository contributor
   - local package consumer
   - victim interaction
2. Record exact security boundary crossed.
3. Record confidentiality impact.
4. Record integrity impact.
5. Record availability impact.
6. Record scope/tenant implications.
7. Separate theoretical escalation from demonstrated escalation.
8. Build a conservative CVSS vector when appropriate.
9. Explain what evidence supports each impact claim.

## Output

```text
HYPOTHESIS:
ATTACKER_PREREQUISITES:
USER_INTERACTION:
BOUNDARY_CROSSED:
CONFIDENTIALITY:
INTEGRITY:
AVAILABILITY:
TENANT_SCOPE:
DEMONSTRATED_IMPACT:
THEORETICAL_IMPACT:
CVSS_VECTOR:
SEVERITY:
RATIONALE:
UNCERTAINTIES:
```

## Rules

- Do not score unproven impact.
- Do not convert "could lead to" into demonstrated impact.
- Prefer reproducible impact over dramatic wording.
- Severity must be revisable if new evidence changes prerequisites or impact.
