---
name: Vercel Version Gate
description: Verify current stable exposure and distinguish current bugs, regressions, incomplete fixes, historical issues, and non-affected versions.
---

# Vercel Version Gate

Use this skill before confirmation and whenever a patch or historical issue is involved.

## When To Use

- Before reporting any OSS candidate.
- When testing a security patch.
- When a changelog or advisory suggests prior coverage.
- When behavior differs across releases.

## Workflow

1. Identify:
   - current stable
   - tested version
   - previous version
   - suspected fixed version
   - latest repository revision if relevant
2. Verify the vulnerable code exists in the tested stable version.
3. Reproduce on current stable.
4. When useful, run the same test against:
   - one previous release
   - suspected fix
   - one release after the fix
5. Classify.

## Classifications

- CURRENT
- FIXED
- REGRESSION
- INCOMPLETE_FIX
- ALTERNATE_PATH
- KNOWN_DUPLICATE
- NOT_AFFECTED
- VERSION_UNKNOWN

## Output

```text
TARGET:
CURRENT_STABLE:
TESTED_VERSION:
AFFECTED_VERSIONS:
NON_AFFECTED_VERSIONS:
FIRST_KNOWN_AFFECTED:
FIX_VERSION:
CLASSIFICATION:
EVIDENCE:
VERDICT:
```

## Rules

- Never report an obsolete-only bug as current.
- Never assume a version from memory.
- Do not infer affected ranges without evidence.
- A patch diff is evidence for where to look, not proof of exploitability.
