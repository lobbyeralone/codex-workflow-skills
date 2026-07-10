---
name: tidy-knowledge-base
description: Use when documentation, prompts, workflows, tool notes, or agent rules are scattered across multiple files and need to be merged into one maintainable knowledge base without secrets or project-specific details.
---

# Tidy Knowledge Base

## Overview

Turn a scattered documentation folder into one practical main document plus a small set of templates. Preserve reusable knowledge and remove duplicate indexes, stale links, secrets, logs, and project-private details.

## Workflow

1. Inventory current files and classify each as main knowledge, template, duplicate index, stale note, or private material.
2. Choose one main document. Organize it by daily use: how to ask, available tools, skill selection, engineering rules, workflows, prompts, and maintenance.
3. Merge only reusable content. Collapse repeated rules into one section.
4. Move copyable skeletons into `templates/`. Do not keep large tutorial fragments in the main document.
5. Delete or archive old numbered documents only after the main document covers their useful content.
6. Update the root README to point to the single main document and templates.
7. Verify with scans for stale links, secrets, absolute paths, project names, unfinished placeholders, and duplicate entry points.

## Output Contract

Report:

- Main document path.
- Files kept, merged, deleted, or moved.
- Verification commands and results.
- Remaining risks or intentionally excluded content.

## Common Mistakes

- Keeping every old file "just in case".
- Turning the main document into a full archive instead of a working guide.
- Copying authentication notes, logs, session history, private paths, or project-specific rules.
- Declaring completion before link and sensitive-content scans.
