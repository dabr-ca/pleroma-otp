# Pleroma OTP Builder

This repository builds a OTP tarball for upstream Pleroma using GitHub Actions.

Run **Build Pleroma OTP** manually from the Actions tab and provide an upstream
Pleroma tag, for example `v2.10.2`. The workflow clones
`https://git.pleroma.social/pleroma/pleroma.git`, checks out that exact tag,
builds the OTP release with the same core steps as upstream Woodpecker, and
publishes:

- `pleroma-otp-<tag>-arm64-run-<run_id>-attempt-<run_attempt>.tar.gz`

For Ansible, use the immutable release asset URL from the GitHub release:

```text
https://github.com/<owner>/<repo>/releases/download/pleroma-otp-<tag>-arm64-run-<run_id>-attempt-<run_attempt>/pleroma-otp-<tag>-arm64-run-<run_id>-attempt-<run_attempt>.tar.gz
```

The tarball contains the contents of Pleroma's generated `release/` directory,
not the `release/` directory itself. Extract it directly into `/opt/pleroma`.
