# Pleroma Artifact Builder

This repository builds GitHub Release assets for upstream
[Pleroma](https://git.pleroma.social) projects.

All workflows are manual. Each run publishes a release whose tag includes the
source ref, GitHub Actions run ID, and run attempt, so the resulting
`/releases/download/<tag>/<asset>` URL is stable and never overwritten.

## Pleroma OTP

Run **Build Pleroma OTP** with an upstream Pleroma tag, for example `v2.10.2`.
The workflow clones `https://git.pleroma.social/pleroma/pleroma.git`, checks
out that tag, and builds an arm64 OTP release using the same core steps as
upstream Woodpecker.

- release tag: `pleroma-otp-<tag>-arm64-run-<run_id>-attempt-<run_attempt>`
- asset: `pleroma-otp-<tag>-arm64.tar.gz`

This tarball is consumed by
[`dabr-ca/config`](https://github.com/dabr-ca/config/blob/013018ad994cfb9a16489fc62be16cafc91fc43f/roles/pleroma/defaults/main.yaml#L2-L3).

## Pleroma FE

Run **Build Pleroma FE** with an upstream Pleroma FE ref, for example
`develop`. The workflow clones
`https://git.pleroma.social/pleroma/pleroma-fe.git`, resolves the ref to a
commit, and builds with Node.js 20.19.0 and Yarn 1.22.22.

- release tag: `pleroma-fe-<sanitized-ref>-<short-sha>-run-<run_id>-attempt-<run_attempt>`
- asset: `pleroma-fe-<sanitized-ref>-<short-sha>.zip`

The zip keeps `dist/` as its top-level directory, matching Pleroma's default
frontend installer `build_dir`.
