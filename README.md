# Pleroma OTP Builder

This repository builds a OTP tarball for upstream Pleroma using GitHub Actions.

Run **Build Pleroma OTP** manually from the Actions tab and provide an upstream
Pleroma tag, for example `v2.10.2`. The workflow clones
`https://git.pleroma.social/pleroma/pleroma.git`, checks out that exact tag,
builds the OTP release with the same core steps as upstream Woodpecker, and
publishes:

- `pleroma-otp-<tag>-arm64-run-<run_id>-attempt-<run_attempt>.tar.gz`

The release URL is immutable. The tarball is used by [`dabr-ca/config`](https://github.com/dabr-ca/config/blob/013018ad994cfb9a16489fc62be16cafc91fc43f/roles/pleroma/defaults/main.yaml#L2-L3).
