---
name: Vercel Change Intelligence
description: Turn recent Vercel releases, commits, changed files, and product signals into a ranked list of concrete security-relevant research hypotheses.
---

# Vercel Change Intelligence

Use this skill to identify what changed recently and convert those changes into precise security questions.

## When To Use

- At the start of a new Vercel OSS cycle.
- After a new stable release.
- When `vercelhunt intel diff` reports changes.
- When a previously tested-secure hypothesis may need reopening.
- Before generic vulnerability scanning.

## Preferred Commands

```bash
./vercelhunt intel sync
./vercelhunt intel diff
./vercelhunt intel plan

./vercelhunt program use vercel-open-source
./vercelhunt oss plan --limit 20
./vercelhunt oss intel TARGET --since '30 days ago'
./vercelhunt oss hypotheses TARGET
./vercelhunt oss next
```

## Workflow

1. Identify the current stable release and repository revision.
2. Collect recent release, commit, and changed-file signals.
3. Highlight changes touching:
   - authorization
   - authentication
   - tenant/project/team identity
   - redirects and URL parsing
   - request routing
   - filesystem paths
   - archive extraction
   - build/deploy boundaries
   - cache keys
   - serialization
   - tool execution
   - workflow state
   - sandbox lifecycle
   - credentials/secrets
   - network policy
4. Map each changed file to a trust boundary.
5. Ask what security property the change is trying to preserve.
6. Generate falsifiable hypotheses, not generic bug classes.
7. Rank by:
   - reachability
   - attacker control
   - boundary sensitivity
   - current stable exposure
   - likelihood of incomplete sibling coverage
8. Send the strongest hypothesis to Source Trace.

## Hypothesis Format

```text
ID:
TARGET:
VERSION:
CHANGE:
TRUST_BOUNDARY:
ATTACKER_CONTROLLED_INPUT:
EXPECTED_GUARD:
POTENTIAL_SINK:
SECURITY_PROPERTY:
TEST:
KILL_CONDITION:
WHY_NOW:
```

## Rules

- A changed line is not a vulnerability.
- A security commit is a patch oracle, not proof.
- Prefer one strong hypothesis over many shallow ones.
- Reopen TESTED_SECURE only when the changed code can affect the prior security property.
