<!-- dazl:workspace-details:start -->
# This workspace

You are working in a Dazl **session root**: a git repository that holds the whole workspace.
Each repository below is a first-level directory with its own git history, and everything
outside them — this file, the configuration, the setup tree — belongs to the workspace
repository itself. Run `git submodule status` to see which of them the session repo tracks:
a repository with no commit yet is deliberately left untracked until it has one.

- **Workspace repository:** `https://github.com/evgeny-pai/dazl-workspace-dazl-dev.git`
- **Configuration:** `dazl.config.json` at the workspace root — every path in it is relative to that root.
- **Primary app:** `dazl/`

### Repositories

| Directory | Remote | Setup directory |
| --- | --- | --- |
| `api-server/` | `https://github.com/dazl-dev/api-server` | `dazl-setup/api-server/` |
| `dazl/` | `https://github.com/dazl-dev/dazl` | `dazl-setup/dazl/` |

### Apps

| App id | Runs from |
| --- | --- |
| `dazl` | `dazl` |
| `root` | `.` |

### Where things live

- `.agents/skills/` — skills compounded while working here. One flat pool for the whole
  workspace; write a lesson as `<name>.md` (or `<name>/SKILL.md`) with `name` and `description` frontmatter.
- `dazl-setup/<repo>/` — Dazl's per-repo setup: the hooks file and the generated vite configs.
  It is deliberately outside the repositories, so nothing Dazl owns lands in a user repository.
- Each repository keeps its own instructions (`AGENTS.md`, `CLAUDE.md`, `.agents/`). This file describes
  the workspace around them and never replaces them.
<!-- dazl:workspace-details:end -->
