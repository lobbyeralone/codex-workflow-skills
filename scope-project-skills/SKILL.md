---
name: scope-project-skills
description: Use when globally installed skills contain project-specific behavior, names, paths, workflows, or domain rules that may trigger in unrelated repositories and should be moved under a project-local skills directory.
---

# Scope Project Skills

## Overview

Move project-specific skills out of the global skill namespace and into the owning repository. Keep only a lightweight global router or instruction that checks the current workspace before loading project rules.

## Workflow

1. List globally installed skills and identify candidates that mention a single project, repository, domain model, private workflow, or project path.
2. Confirm the target repository root using read-only checks.
3. Create a project-local skills directory such as `.codex-project/skills`.
4. Move only the project-specific skill folders. Do not move general-purpose skills.
5. Update any global router or project instructions to load those skills only after confirming the current working directory is inside that project.
6. Validate each moved skill's frontmatter.
7. Scan global skill metadata to confirm the project-specific skills no longer appear globally.

## Safety Rules

- Never apply one project's rules outside its repository root.
- Do not publish private project names, paths, protocol numbers, schemas, credentials, or business context.
- If the target directory already contains a skill with the same name, stop and inspect before overwriting.
- Keep the router generic: routing behavior is reusable, project details are not.

## Output Contract

Report:

- Skills moved.
- New project-local location.
- Router or instruction changes.
- Validation command results.
- Any skipped skills and why.
