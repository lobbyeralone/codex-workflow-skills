---
name: audit-completion-evidence
description: Use when an agent is about to claim a task, goal, fix, migration, install, or documentation update is complete and must prove each requirement with current evidence before reporting success.
---

# Audit Completion Evidence

## Overview

Prevent premature completion claims. Convert the user's request into verifiable requirements, gather fresh evidence for each one, and continue work when evidence is missing or weak.

## Audit Steps

1. Restate the original objective without narrowing it.
2. Split it into concrete requirements, deliverables, commands, gates, and constraints.
3. For each item, name the evidence that would prove completion.
4. Inspect current files, command output, rendered artifacts, runtime behavior, or external state as appropriate.
5. Mark each item as proven, contradicted, incomplete, weak evidence, or missing evidence.
6. Continue working on incomplete or weak items before claiming completion.
7. Report the final checklist with evidence.

## Evidence Rules

- Current command output beats memory.
- File existence does not prove behavior.
- A passing narrow check does not prove a broad requirement.
- "Looks fine", "should work", and prior intent are not evidence.
- If verification cannot run, state the blocker and provide the strongest available substitute evidence.

## Output Contract

Use this shape:

```text
Requirement:
Evidence:
Status:
Gap or risk:
```

Only claim completion when every required item is proven.
