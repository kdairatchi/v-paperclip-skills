---
name: Vercel Report Builder
description: Convert a fully verified Vercel finding into a concise HackerOne-ready report with exact reproduction, controls, evidence, impact, affected versions, and scope context.
---

# Vercel Report Builder

Use this skill only after Scope Guard, Evidence Gate, Version Gate, Duplicate Check, and Severity Review are complete.

## When To Use

- Candidate status is CONFIRMED.
- Duplicate classification is CLEAR or manually cleared.
- Current stable exposure is proven.
- Scope is verified.

## Report Structure

1. Title
2. Summary
3. Affected component/version
4. Attacker prerequisites
5. Root cause
6. Security boundary crossed
7. Reproduction
8. Baseline/control
9. Negative control
10. Observed impact
11. Evidence
12. Suggested severity
13. Remediation direction

## Writing Rules

- State facts before conclusions.
- Use exact commands and minimal PoC.
- Include harmless identifiers/markers.
- Redact tokens and secrets.
- Do not bury prerequisites.
- Do not inflate severity.
- Do not include unnecessary destructive actions.
- Keep the root cause distinct from the symptom.

## Readiness Checklist

```text
[ ] Current stable affected
[ ] In scope
[ ] Exact root cause
[ ] Reachability proven
[ ] Guard failure proven
[ ] Security boundary crossed
[ ] Meaningful impact
[ ] Baseline
[ ] Negative control
[ ] Clean reproduction
[ ] Version gate complete
[ ] Duplicate check complete
[ ] Severity review complete
[ ] Evidence redacted
```

## Output

Return:

```text
STATUS: READY | HOLD

TITLE:
SUMMARY:
AFFECTED:
PREREQUISITES:
ROOT_CAUSE:
IMPACT:
REPRODUCTION:
CONTROL:
NEGATIVE_CONTROL:
VERSION_EVIDENCE:
DUPLICATE_EVIDENCE:
SEVERITY:
REMEDIATION_DIRECTION:
BLOCKERS:
```

If any required gate is incomplete, return HOLD.
