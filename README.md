# Open Source Skills

Standalone, project-neutral Codex skills extracted from reusable development workflows.

## Skills

- `tidy-knowledge-base`: consolidate scattered documentation into one maintainable knowledge base.
- `scope-project-skills`: move project-specific skills out of global discovery and into project-local folders.
- `audit-completion-evidence`: require evidence before declaring work complete.

See [RECOMMENDED.md](RECOMMENDED.md) for rationale, evidence, usage scenarios, and expected outcomes.

中文说明见 [RECOMMENDED.zh-CN.md](RECOMMENDED.zh-CN.md)。

## Install

Copy any skill folder into a Codex skills directory, for example:

```powershell
Copy-Item -Recurse .\open-source-skills\audit-completion-evidence $env:USERPROFILE\.codex\skills\
```

Install all three:

```powershell
Copy-Item -Recurse .\open-source-skills\tidy-knowledge-base $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\open-source-skills\scope-project-skills $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\open-source-skills\audit-completion-evidence $env:USERPROFILE\.codex\skills\
```

Restart Codex after installing new skills.
