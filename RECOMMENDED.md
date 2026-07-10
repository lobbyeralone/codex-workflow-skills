# Recommended Skills

These three skills are recommended first because they solve common agent-work problems that appeared repeatedly during real Codex setup and knowledge-base work: scattered context, project-specific skill leakage, and premature completion claims.

## Summary

| Skill | Core problem | Best moment to use | Outcome after use |
| --- | --- | --- | --- |
| `tidy-knowledge-base` | Notes, prompts, workflows, and tool docs are scattered. | When a folder has too many docs or duplicate indexes. | One main knowledge base, templates separated, stale/private content removed. |
| `scope-project-skills` | Project-only skills trigger globally and pollute unrelated tasks. | When a skill mentions one project, repo, domain model, or private workflow. | Project skills move local, global discovery becomes cleaner, routing is safer. |
| `audit-completion-evidence` | Agents claim completion before proving every requirement. | Before saying a task, fix, install, migration, or goal is complete. | Each requirement has evidence, weak gaps are exposed, unfinished work continues. |

## 1. `tidy-knowledge-base`

### Why Recommend It

Most AI-assisted work eventually creates scattered notes: prompts in one file, tool commands in another, workflow checklists somewhere else, and old indexes that no one trusts. This skill turns that mess into one usable main document.

### Evidence

It was extracted from a real consolidation task where multiple numbered knowledge-base files were merged into a single main document with a README and templates directory. The useful pattern was not the specific content, but the repeatable process: inventory, merge, remove duplicates, separate templates, scan links, scan sensitive/private material.

### When To Use

- A documentation folder has too many entry points.
- A README links to many overlapping files.
- Prompts, tool notes, agent rules, and workflows need one source of truth.
- A team wants reusable AI usage guidance without leaking secrets or project details.

### What Happens After Use

- Readers get one main document instead of hunting across many files.
- Reusable prompts and workflows are easier to find.
- Templates stay separate from prose.
- Old links, duplicate indexes, secrets, logs, and project-private details are explicitly checked.

### Typical Request

```text
Use tidy-knowledge-base to merge this documentation folder into one maintainable knowledge base. Keep reusable guidance, separate templates, remove stale links and private material, then report verification results.
```

## 2. `scope-project-skills`

### Why Recommend It

Global skills are convenient until project-specific rules start appearing in unrelated repositories. This skill prevents accidental cross-project behavior by moving project-only skills under the owning repository.

### Evidence

It was extracted from a real cleanup where project-specific skills were moved out of the global skill directory and placed under a project-local `.codex-project/skills` directory. The reusable pattern is safe routing: confirm the current repository first, then load only the relevant local skill.

### When To Use

- A skill name or description clearly belongs to one project.
- A skill contains project-only paths, modules, workflows, protocols, schemas, or domain rules.
- The global skill list is noisy and risks triggering the wrong behavior.
- You want a reusable global router but private project rules should stay local.

### What Happens After Use

- Global skill discovery becomes smaller and safer.
- Project rules only apply inside the matching repository.
- Project-specific details are no longer exposed in general-purpose documentation.
- Future agents are less likely to apply the wrong workflow.

### Typical Request

```text
Use scope-project-skills to move project-specific skills out of global discovery. Confirm the target repository, move them into `.codex-project/skills`, update routing, and validate the moved skills.
```

## 3. `audit-completion-evidence`

### Why Recommend It

The most expensive agent failure is claiming "done" while requirements are only partially satisfied. This skill forces completion to be proven requirement by requirement with current evidence.

### Evidence

It was extracted from repeated goal-completion checks where the task could only be marked complete after verifying the actual files, links, scans, command outputs, and stated requirements. The reusable pattern is evidence before completion, not confidence before verification.

### When To Use

- Before marking a `/goal` complete.
- Before saying a bug fix, migration, install, refactor, or documentation task is done.
- After a long multi-step task where some requirements may have drifted.
- When the user asks for proof, validation, or a final audit.

### What Happens After Use

- The original request is split into verifiable items.
- Each item gets evidence or a clearly stated gap.
- Weak evidence is treated as incomplete rather than silently accepted.
- The agent continues work instead of summarizing too early.

### Typical Request

```text
Use audit-completion-evidence before finalizing this task. Split the original request into requirements, inspect current evidence for each one, continue on missing items, and only claim completion when every item is proven.
```

## Selection Guide

| If your problem is... | Use |
| --- | --- |
| "Our docs are scattered and nobody knows which file matters." | `tidy-knowledge-base` |
| "This skill belongs to one project but keeps showing up everywhere." | `scope-project-skills` |
| "The agent says done, but I am not sure it proved everything." | `audit-completion-evidence` |

## Install Examples

```powershell
Copy-Item -Recurse .\open-source-skills\tidy-knowledge-base $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\open-source-skills\scope-project-skills $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\open-source-skills\audit-completion-evidence $env:USERPROFILE\.codex\skills\
```

Restart Codex after installing new skills.
