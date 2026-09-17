---
name: multi-repo-build-check-gap
description: Load before running or interpreting the build-check tool in a multi-repo Dazl workspace (an `apps` config with no package.json at the workspace root, e.g. the dazl-in-dazl layout with dazl/, api-server/, and a root app entry). Covers why checkBuildErrors fails with ENOENT on /package.json here and what to use instead.
---

# Build-check tool gap in a multi-repo workspace

`checkBuildErrors` runs `npm run build` from the workspace root regardless of `dazl.config.json`'s
`apps`/`primaryApp` settings. In a multi-repo layout where the workspace root itself has no
`package.json` (apps live in first-level repo directories such as `dazl/` and `api-server/`, and any
`root` app entry is a placeholder with no npm project), the tool fails immediately with
`ENOENT: no such file or directory, open '.../package.json'`. This is a tooling gap, not a build
regression — it fails the same way before and after an unrelated change.

**Verify instead with:**
- The `typecheck` tool, which does respect `primaryApp`/app resolution and ran `dazl`'s own
  `npm run typecheck` correctly.
- A manual build from the app directory via `shellTool` when a real production build must be
  confirmed (e.g. `cd dazl && NODE_ENV=development npm run build:web`), understood as a separate,
  possibly slow step — not a substitute for the missing tool coverage.

Do not chase this as a caused-by-my-change failure; confirm first whether the workspace root has a
`package.json` at all before spending a fix attempt on it.
