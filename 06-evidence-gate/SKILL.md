---
name: Vercel Evidence Gate
description: Challenge every Vercel candidate with baseline, attack, negative controls, server-side effects, repeatability, and explicit impact before confirmation.
---

# Vercel Evidence Gate

Use this skill after runtime reproduction and before any candidate can be called CONFIRMED.

## Mindset

Attempt to disprove the candidate first.

## Required Evidence

```text
BASELINE
ATTACK
NEGATIVE CONTROL
SERVER-SIDE OR STATE EFFECT
REPEAT
IMPACT
```

## Workflow

1. Verify exact target/version.
2. Verify the baseline does not show the alleged behavior.
3. Verify the attack changes only the intended variable.
4. Verify the negative control blocks or removes the effect.
5. Verify the effect using server-side/state evidence where possible.
6. Repeat from a clean state.
7. Verify the impact is a security boundary, not merely an error.
8. Separate:
   - observation
   - root cause
   - exploitability
   - impact
9. Reject unsupported severity claims.

## Output

```text
HYPOTHESIS:
VERSION:

REACHABILITY:
GUARD_BYPASS:
BASELINE:
ATTACK:
NEGATIVE_CONTROL:
SERVER_STATE:
REPEATABILITY:
IMPACT:
CLEAN_REPRO:

MISSING:
VERDICT:
```

Allowed verdicts:

- CONFIRMED
- DEEPEN
- INCONCLUSIVE
- KILL

## Fail-Closed Rules

Do not return CONFIRMED if any are missing:

- affected stable version
- runtime reproduction
- meaningful impact
- negative control
- clean repeat
- evidence of the claimed boundary crossing
