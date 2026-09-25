# core — agent guide

Personal workspace that pulls the `ValentinHoracek.Core` repositories into one place.
Nothing depends on this repo. Apps consume individual packages (for example `core-architecture` from NuGet), never `core` itself.

## Repositories

All repositories are git submodules under `lib/`. They are independent of each other.

| Path | Purpose | Status |
|---|---|---|
| `lib/core-agentic` | Source of the `core-agentic` Claude Code plugin (skills) | Active |
| `lib/core-architecture` | NuGet package of ArchUnitNET architecture rules | Active |
| `lib/core-docs` | Automatic documentation generation (DocFx-like; tool not chosen) | Placeholder |
| `lib/core-qa` | Testing (scope not decided) | Placeholder |
| `lib/core-devops` | CI/CD pipeline templates | Placeholder |

Placeholders contain only a README. Do not add content to them unless asked.

Each active repository has its own `AGENTS.md` with repo-specific rules. Read it before changing that repository.

## Working with submodules

- After cloning: `git submodule update --init`.
- Each submodule is a separate git repository. `git submodule update` leaves it in detached HEAD; run `git checkout main` inside it before committing.
- To change a submodule: commit inside the submodule first, then commit the updated pointer in `core`.
- Skills are edited only in `lib/core-agentic`. There are no skill copies elsewhere.
- Do not push unless asked.

## Environment

- The repository is on a Windows drive (`/mnt/c/...`) and is used from WSL.
- `.gitattributes` enforces LF line endings. If files show as modified with no visible change, run `git add --renormalize .`.
- .NET: use `dotnet.exe` (Windows). `dotnet` is not installed in WSL. Building `core-architecture` requires the .NET 10 SDK.

## Local-only files

`.gitignore` excludes `docs/` (specs and plans), `core-workspace.code-workspace` and `.claude/settings.local.json`.
