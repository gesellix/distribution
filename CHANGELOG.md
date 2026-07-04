# Changelog

Notable changes in this fork of [distribution/distribution](https://github.com/distribution/distribution).
For upstream release notes see the files under [`releases/`](./releases).

## Unreleased

#### Storage
- filesystem: make the driver work on Windows, where every blob upload previously failed with HTTP 500. The upload writer is now closed before `startedat` is renamed into place (Windows refuses to rename a file while a handle to it is open), storage keys are treated as slash-separated at the OS boundary, and build-tagged helpers are added for directory sync (a no-op on Windows) and rename (falls back to remove-then-rename on Windows). Also adds a `windows-latest` unit-test CI job. Fixes [distribution/distribution#4901](https://github.com/distribution/distribution/issues/4901). ([#1](https://github.com/gesellix/distribution/pull/1))

#### CI / Release
- Publish self-contained artifacts from this fork: Windows `.exe` release binaries (`windows/amd64`, `windows/arm64`) and multi-arch plus WCOW (nanoserver `ltsc2022`/`ltsc2025`) container images to GHCR (`ghcr.io/gesellix/distribution`), fused into a single multi-os manifest. Docker Hub publishing is gated behind the `DOCKERHUB_ENABLED` repository variable (off by default). Related: [distribution/distribution#3714](https://github.com/distribution/distribution/issues/3714). ([#2](https://github.com/gesellix/distribution/pull/2))
