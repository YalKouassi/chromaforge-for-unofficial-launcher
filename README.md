# Chromaforge for Craft Unofficial Launcher

**An unofficial mirror** of [Chromaforge](https://github.com/emmertex/chromaforge) releases, maintained by
[YalKouassi](https://github.com/YalKouassi), so that
[Craft Unofficial Launcher](https://github.com/YalKouassi/craft-unofficial-launcher) can install
and update Chromaforge.

This repo is **not affiliated with, endorsed by or supported by the Chromaforge contributors** (the authors of Chromaforge),
**or by ArtCraft**. Report problems with Chromaforge itself upstream at
<https://github.com/emmertex/chromaforge>; report problems with this mirror here.

## What this repo publishes

The packages in this repo's releases are **Chromaforge's own builds**, as published on
[emmertex/chromaforge's releases](https://github.com/emmertex/chromaforge/releases). Nothing is rebuilt and no program file is
changed. Each release here:

- downloads upstream's packages and verifies each one before using it;
- renames them to the launcher's `<id>-<version>-<os>-<arch>` naming and, only where the launcher
  couldn't install an archive's layout, repacks that archive (the same files with the same bytes,
  in different folders);
- adds `craft-app.json`, the icon, `SHA256SUMS.txt`, and upstream's licence files from the same tag.

The notes of each release list every file, the upstream asset it came from, its SHA-256, and
whether it was repacked, so you can compare it with upstream's release.

### For Chromaforge

Upstream still names its packages and executable `lightcraft-classic`, the project's former
name. The packages are **renamed** from `lightcraft-classic-<v>-<os>-<arch>` to
`chromaforge-<v>-<os>-<arch>` and otherwise mirrored **byte for byte**; `craft-app.json` lists
`lightcraft-classic` as a former id so the launcher finds `lightcraft-classic.exe` in the portable
zip. Every download is checked against upstream's `SHA256SUMS.txt` first.

Not mirrored: the CLI-only, web and Android builds, the `.zsync` files, `latest.json`, `SHA256SUMS.txt.sig`, and the Linux tarball (its binary isn't named `chromaforge`, so the launcher couldn't install it; Linux gets the AppImage, deb, rpm and Flatpak).

## How it runs

[`.github/workflows/bridge.yml`](.github/workflows/bridge.yml) runs every 30 minutes. It uses
[craft-bridge](https://github.com/YalKouassi/craft-bridge) with [`bridge.toml`](bridge.toml) to
check upstream's latest release and mirror it if this repo doesn't have it yet. If upstream starts
publishing its own `craft-app.json`, the bridge stops publishing, and the launcher should point at
upstream directly.

Using this mirror means trusting its maintainer as well as upstream; see
[craft-bridge's Trust section](https://github.com/YalKouassi/craft-bridge#trust).

## Licences

Chromaforge is licensed by its authors under MIT (with a NOTICE file); each release attaches upstream's licence files.
This repo's own files (the config, workflow and this README) are available under MIT OR
Apache-2.0 ([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)).
