<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
    <img src="assets/logo.svg" alt="danio" width="300">
  </picture>
</p>

<p align="center">
  <strong>Render Blender projects anywhere — your desk, the office render room, or a rented GPU.</strong>
</p>

<p align="center">
  <a href="https://github.com/danio-app/danio-releases/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/danio-app/danio-releases?filter=v*&label=release"></a>
  <a href="https://github.com/danio-app/danio-releases/actions/workflows/release.yml"><img alt="Release" src="https://github.com/danio-app/danio-releases/actions/workflows/release.yml/badge.svg"></a>
  <a href="https://github.com/danio-app/danio-releases/actions/workflows/ffmpeg.yml"><img alt="FFmpeg" src="https://github.com/danio-app/danio-releases/actions/workflows/ffmpeg.yml/badge.svg"></a>
  <img alt="Platforms" src="https://img.shields.io/badge/platforms-Windows%20%7C%20Linux-informational">
</p>

<p align="center">
  <a href="https://danio.app">Website</a> ·
  <a href="https://danio.app/en/docs">Docs</a> ·
  <a href="https://github.com/danio-app/danio-releases/releases">All releases</a> ·
  <a href="mailto:support@danio.app">support@danio.app</a>
</p>

---

This repository publishes danio's builds. The Release workflow tests, builds and signs every version here, and danio updates itself from these releases. To get started, download from [danio.app](https://danio.app).

## Install

**Linux**

```bash
curl -fsSL https://danio.app/install.sh | sh
```

**Windows** (PowerShell)

```powershell
powershell -ExecutionPolicy Bypass -c "irm https://danio.app/install.ps1 | iex"
```

Or download the latest build directly:

| Platform | x64 | ARM64 |
| --- | --- | --- |
| Windows | [danio-windows-amd64.exe](https://danio.app/download/windows) | [danio-windows-arm64.exe](https://danio.app/download/windows-arm64) |
| Linux | [danio-linux-amd64](https://danio.app/download/linux) | [danio-linux-arm64](https://danio.app/download/linux-arm64) |
| Blender add-on | [danio-blender-addon.zip](https://danio.app/download/addon) | |

danio installs the Blender add-on for you; the zip is for installing it by hand.

## What a release holds

| File | What it is |
| --- | --- |
| `danio-<os>-<arch>` | danio for Windows and Linux, x64 and ARM64 |
| `danio-blender-addon-<version>.zip` | The Blender add-on |
| `SHA256SUMS` | The SHA-256 of every file |
| `release.json`, `release.json.sig` | The release as danio reads it, and its Ed25519 signature |
| `compose.yaml` | Docker Compose for running danio as a host |

danio only installs an update whose `release.json` carries a valid signature, and checks every file against the hashes in it, so a changed download or mirror can't swap the program.

## Docker

`ghcr.io/danio-app/danio` runs danio as a workspace host on a NAS or a server, for x64 and ARM64. Each release carries a `compose.yaml`: map the data volume and the NAS's shares, then `docker compose up -d`.

| Tag | Follows |
| --- | --- |
| `latest` | the latest release |
| `rc` | the latest pre-release or release |
| `<version>` | that version |

## FFmpeg

The `ffmpeg-*` releases are danio's own FFmpeg: a small, fully static build with only what danio needs, for Linux and Windows on x64 and ARM64. danio workspaces fetch it by themselves.

The FFmpeg workflow builds it from [`ffmpeg/build.sh`](ffmpeg/build.sh), checks each build on its own platform ([`ffmpeg/check.py`](ffmpeg/check.py)) and publishes it with a signed `ffmpeg.json`. FFmpeg built with x264 is licensed under the GPL; each release carries the sources it was built from.

## Links

- [Terms of Service](https://danio.app/en/terms) · [Privacy Policy](https://danio.app/en/privacy)
- Questions and support: [support@danio.app](mailto:support@danio.app)
