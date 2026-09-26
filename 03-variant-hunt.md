---
name: Vercel Variant Hunter
description: Search Vercel code for sibling paths, alternate parsers, lifecycle branches, and incomplete security-fix coverage around a proven security boundary.
---

# Vercel Variant Hunter

Use this skill after identifying a security-sensitive code path, patch, or guard.

## When To Use

- A security fix exists.
- One route or method has a new guard.
- A parser/normalizer was hardened.
- A lifecycle state gained validation.
- A finding was previously fixed and may have alternate paths.

## Core Question

Do not ask only:

> Is this function vulnerable?

Ask:

> Where else does the same security property need to be enforced?

## Variant Families

Check for:

- sibling HTTP methods
- sync vs async implementations
- CLI vs SDK paths
- REST vs internal RPC paths
- preview vs production behavior
- create/update/resume/restore/delete asymmetry
- local vs remote execution paths
- old/new API versions
- alternate parsers
- redirect hops
- URL normalization differences
- encoded/decoded variants
- filesystem canonicalization differences
- cache warm/cold paths
- region/failover paths
- snapshot/currentSnapshotId differences
- free/enterprise or feature-flag branches
- different package adapters/providers

## Workflow

1. Identify the protected security property.
2. Identify the newly added or existing guard.
3. Search for callers and sibling implementations.
4. Search for alternate normalization/parsing code.
5. Compare guard ordering.
6. Compare state assumptions.
7. Generate one variant hypothesis per meaningful divergence.
8. Kill variants that share the same dominating guard.
9. Send surviving variants to Source Trace or Local Reproduction.

## Output

```text
ROOT_PATH:
SECURITY_PROPERTY:
PRIMARY_GUARD:
SIBLINGS_CHECKED:
ALTERNATE_PARSERS:
LIFECYCLE_VARIANTS:
STATE_VARIANTS:
SURVIVING_VARIANTS:
KILLED_VARIANTS:
NEXT_HYPOTHESIS:
```

## Rules

- Never submit a known original issue as a new finding.
- A variant must have a distinct reachable exploit path or incomplete fix.
- Similar code is not sufficient; prove different security behavior.
