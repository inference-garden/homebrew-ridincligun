# Releasing — maintainer runbook

How a new ridinCLIgun version becomes a poured bottle. Three steps are manual
(by design — a human gates every commit); the heavy lifting runs in CI.

## Per release

1. **Prerequisite:** the new version is tagged and pushed in the app repo
   (`inference-garden/ridinCLIgun`, tag `vX.Y.Z`).

2. **Bump the formula** (commit to `main`, or via PR so the from-source
   workflow validates it first):
   - update `url` and `sha256` to the new tag,
   - regenerate the `resource` blocks if any dependency changed,
   - **remove the existing `bottle do … end` block** — its checksums belong
     to the previous version. The bottle workflow refuses to run while a
     stale block is present.

3. **Run the Bottle workflow:** Actions tab → *Bottle* → *Run workflow*
   (branch `main`). It builds the bottles on the supported macOS/architecture
   matrix (~15 min), creates the GitHub Release `vX.Y.Z` on this repo with
   the bottle files as assets, and opens a PR titled *"Add bottles for
   X.Y.Z"*.

4. **Review and merge the bottle PR.** The diff must touch only the
   `bottle do` block. Checksums are CI-generated — never hand-edit them; if
   something looks wrong, re-run the workflow instead.

5. **Verify:** merging triggers the pour-test workflow (clean runners must
   pour, no rust/llvm, `--version` works, tap-trust gate behaves). For a
   real-world check: `brew update && brew upgrade ridincligun` on any Mac
   should report `Pouring ridincligun--X.Y.Z…`.

## Notes

- **CI commit identity:** the bottle PR's commit is authored by
  `github-actions[bot]` — machine-made commits stay distinguishable from
  maintainer commits. Identity-leak checks that expect personal noreply
  addresses must allowlist exactly
  `41898282+github-actions[bot]@users.noreply.github.com`.
- **Re-bottling the same version** (rare): delete the `bottle do` block and
  the release's `*.bottle.tar.gz` assets, then re-run the workflow. If users
  may already have poured the old bottles, bump the formula `revision`
  instead of silently replacing assets.
- **Hosting:** bottles are plain release assets on this repo; the formula's
  `root_url` points at `releases/download/vX.Y.Z`. Moving hosts later only
  means changing `root_url` in a future release.
- **Supply chain:** workflow actions are pinned to full commit SHAs; bump
  them deliberately, not via floating tags.
