# io.github.read-flow

Flathub submission repo for [Read Flow](https://github.com/read-flow/read-flow), a local-first
document archive organizer for e-books and PDFs.

## Building

```bash
flatpak-builder --user --install --force-clean build-dir io.github.read-flow.yml
```

`flatpak-builder` needs Linux (bubblewrap-based sandboxing) — this can't be built or tested on
macOS. The manifest's build logic is otherwise identical to the one verified working in the main
repo's CI (`.github/workflows/release.yml`, job `build-flatpak`); only the source pin (`type: git`
here vs. a local checkout there) differs.

## Files

- `io.github.read-flow.yml` — the manifest.
- `cargo-sources.json` / `node-sources.json` — offline vendoring sources for cargo/npm, generated
  with the official [flatpak-builder-tools](https://github.com/flatpak/flatpak-builder-tools)
  generators against the main repo's `Cargo.lock` / `pwa/package-lock.json`. Regenerate these on
  every release (see the maintenance notes at the top of the manifest).

## Status

Not yet submitted to Flathub. Manifest logic is CI-verified (main repo); this repo's own
`type: git` source pin has not been build-tested (needs a Linux machine with `flatpak-builder`).
