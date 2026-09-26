---
name: Vercel Local Reproduction
description: Build minimal, deterministic local reproductions for Vercel OSS hypotheses using stable releases, controlled fixtures, and harmless markers.
---

# Vercel Local Reproduction

Use this skill when a hypothesis is source-reachable and needs runtime confirmation.

## When To Use

- For VERCEL OSS hypotheses.
- Before any live-platform validation where local proof is possible.
- When comparing affected and fixed versions.
- When validating parser, filesystem, build, routing, cache, workflow, or tool behavior.

## Workflow

1. Confirm Scope Guard verdict is PROCEED.
2. Confirm exact stable version.
3. Create an isolated fixture.
4. Record baseline behavior.
5. Mutate one variable only.
6. Use harmless markers.
7. Capture:
   - command
   - version
   - input
   - stdout/stderr
   - exit code
   - filesystem/state changes
8. Run negative control.
9. Repeat from clean state.
10. If useful, compare adjacent versions.

## Evidence Layout

Prefer:

```text
evidence/confirmed/<HYPOTHESIS>/
  baseline.txt
  attack.txt
  negative-control.txt
  version.txt
  state-before.txt
  state-after.txt
  verdict.json
```

## Reproduction Standard

A PASS requires:

```text
[ ] exact version recorded
[ ] deterministic setup
[ ] baseline captured
[ ] attack differs by one intentional mutation
[ ] observable security-relevant effect
[ ] negative control
[ ] clean repeat succeeds
```

## Verdicts

- PASS
- FAIL
- INCONCLUSIVE
- EXEC_ERROR
- KILL

## Safety

- Local fixtures first.
- Synthetic secrets only.
- Do not use real customer data.
- Do not turn a local code-execution primitive into destructive behavior.
- Stop once the security property is proven.
