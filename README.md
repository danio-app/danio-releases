# danio releases

Builds of [danio](https://danio.learnder.org), published by its Release workflow. danio updates itself from here; download it from https://danio.learnder.org.

## Docker

`ghcr.io/loudomian/danio` runs danio as a workspace host on a NAS or a server, for x64 and ARM64. Each release carries a `compose.yaml` for it: map the data volume and the NAS's shares, then `docker compose up -d`. Tags: the version, `rc` (the latest pre-release or release) and `latest` (the latest release).

## FFmpeg

The `ffmpeg-*` releases are danio's own FFmpeg: a small, fully static build with only what danio needs, for Linux and Windows on x64 and ARM64. danio workspaces fetch it by themselves. FFmpeg built with x264 is licensed under the GPL; the recipe is [`ffmpeg/build.sh`](ffmpeg/build.sh), and each release carries the sources it was built from. The FFmpeg workflow builds it, checks each build on its own platform ([`ffmpeg/check.py`](ffmpeg/check.py)) and publishes it with a signed `ffmpeg.json`.
