---
name: Vercel Duplicate Check
description: Check Vercel candidates against public issues, pull requests, advisories, CVEs, changelogs, and prior fixes before report promotion.
---

# Vercel Duplicate Check

Use this skill after impact is demonstrated and before report-ready status.

## When To Use

- Every confirmed candidate.
- Any patch-oracle or regression hunt.
- Any issue with similar public fixes.
- Before writing the final report.

## Search Areas

- repository issues
- repository pull requests
- merged security-related changes
- release notes/changelog
- GitHub Security Advisories
- CVE records
- Vercel security advisories
- public writeups/disclosures when relevant

## Workflow

1. Extract distinctive identifiers:
   - function names
   - route names
   - error strings
   - feature names
   - security property
   - affected component
2. Search exact identifiers first.
3. Search the root cause, not only the final symptom.
4. Search closed issues and merged PRs.
5. Check adjacent versions and old feature names.
6. Compare:
   - root cause
   - entrypoint
   - guard failure
   - sink
   - impact
7. Classify.

## Classifications

- CLEAR
- POSSIBLE_DUPLICATE
- DUPLICATE
- KNOWN_FIX_VARIANT
- REGRESSION_CANDIDATE
- NEEDS_MANUAL_REVIEW

## Output

```text
HYPOTHESIS:
SEARCH_TERMS:
ISSUES_CHECKED:
PRS_CHECKED:
ADVISORIES_CHECKED:
CVES_CHECKED:
CHANGELOG_CHECKED:
CLOSEST_MATCH:
ROOT_CAUSE_MATCH:
PATH_MATCH:
CLASSIFICATION:
NOTES:
```

## Rules

- Similar symptoms do not automatically mean duplicate.
- A distinct alternate path may be a valid variant.
- If uncertain, classify NEEDS_MANUAL_REVIEW rather than CLEAR.
