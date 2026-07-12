# io.github.read-flow

Flathub submission repo for [Read Flow](https://github.com/read-flow/read-flow), a local-first
document archive organizer for e-books and PDFs.

## Building

```bash
flatpak-builder --user --install --force-clean build-dir io.github.read-flow.yml
```

The build logic (SDK extensions, toolchain install, build commands) is identical to the manifest
verified working in the main repo's CI (`.github/workflows/release.yml`, job `build-flatpak`) —
confirmed green end-to-end on v0.1.1, including mupdf's full C/C++ compile and the entire
libcosmic/wgpu/sqlx stack (run 29185080376). Only the `sources:` entry for the app itself differs
here: a `type: git` pin to a release tag/commit, instead of the local checkout CI uses.

## Files

- `io.github.read-flow.yml` — the manifest.
- `cargo-sources.json` / `node-sources.json` — offline vendoring sources for cargo/npm, generated
  with the official [flatpak-builder-tools](https://github.com/flatpak/flatpak-builder-tools)
  generators against the main repo's `Cargo.lock` / `pwa/package-lock.json`. Regenerate these on
  every release (see the maintenance notes at the top of the manifest).

## Status

Manifest and build logic verified via the main repo's CI. Submitting to Flathub itself (a PR
against `github.com/flathub/flathub`) is the next step.
