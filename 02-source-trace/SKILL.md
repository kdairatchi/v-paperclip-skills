---
name: Vercel Source Trace
description: Trace attacker-controlled data through Vercel code from source to normalization, guards, state transitions, and security-sensitive sinks.
---

# Vercel Source Trace

Use this skill when a concrete hypothesis exists and the team needs to prove or disprove code-level reachability.

## When To Use

- After Change Intelligence creates a concrete hypothesis.
- When a suspicious sink is found.
- When a guard appears incomplete.
- When a sibling route may enforce different authorization or validation.
- Before writing a PoC.

## Required Trace

```text
SOURCE
→ NORMALIZER/PARSER
→ STATE
→ GUARD
→ CALLER
→ SINK
→ OBSERVABLE EFFECT
```

## Workflow

1. Identify the attacker-controlled source.
2. Trace every transformation of the value.
3. Record:
   - type conversions
   - decoding
   - normalization
   - canonicalization
   - validation
   - allowlists/denylists
   - default values
4. Identify state transitions:
   - request context
   - environment
   - filesystem
   - database
   - cache
   - workflow state
   - deployment state
5. Identify every guard:
   - authentication
   - authorization
   - tenant/project/team ownership
   - path containment
   - protocol/host allowlist
   - signature/token
   - lifecycle state
6. Find the sensitive sink.
7. Determine whether attacker influence survives all guards.
8. Produce a precise reachability verdict.

## High-Value Vercel Sinks

- command/process execution
- filesystem write/read/delete
- archive extraction
- network fetch/proxy
- credential/token use
- cross-team/project resource access
- build/deploy artifact mutation
- cache key construction
- redirect destination
- workflow execution
- sandbox lifecycle mutation
- snapshot restore/selection
- plugin/tool execution

## Output

```text
HYPOTHESIS:
SOURCE:
NORMALIZATION:
STATE:
GUARDS:
CALLER:
SINK:
ATTACKER_INFLUENCE:
REACHABLE:
MISSING_PROOF:
VERDICT:
```

`VERDICT`:
- DEEPEN
- READY_FOR_VARIANT_HUNT
- READY_FOR_REPRO
- KILL

## Kill Rules

Kill when:
- the source is not attacker-controlled,
- the sink is unreachable,
- a complete guard dominates the sink,
- the path exists only in an obsolete/non-stable version,
- the observed value cannot influence a security-sensitive argument.
