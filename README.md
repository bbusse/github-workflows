# github-workflows

Reusable GitHub Actions workflows.

## Third-party actions

Every third-party action is code we do not control running with our tokens, so
the default is a plain `run:` step, or a composite action under
`.github/actions/` when the same step is needed twice. Reach for a third-party
action only when neither can do the job, and say in a comment why.

The ones below stay because a `run:` step genuinely cannot replace them:

- `actions/checkout`, `actions/upload-artifact`, `actions/download-artifact`
  reach APIs the runner exposes to actions only.
- `actions/setup-go` selects a specific Go toolchain; the preinstalled Go
  cannot.
- `docker/build-push-action` is what makes `cache-from: type=gha` work — the
  cache credentials are handed to actions, not to `run:` steps.
- `docker/setup-buildx-action` and `docker/setup-qemu-action` do privileged
  runner setup.
- `aws-actions/*` perform the OIDC credential exchange for ECR.
- `vmactions/freebsd-vm` runs a FreeBSD VM around the build.
- `bbusse/container-extract` is ours.

All are pinned to a commit SHA. This table lists the version each SHA
corresponds to and the number of files that use it.

| Action | Version | Users |
| --- | --- | --- |
| [actions/checkout](https://github.com/actions/checkout) | v7.0.1 | 32 |
| [actions/download-artifact](https://github.com/actions/download-artifact) | v8.0.1 | 5 |
| [actions/setup-go](https://github.com/actions/setup-go) | v7.0.0 | 2 |
| [actions/setup-python](https://github.com/actions/setup-python) | v7.0.0 | 1 |
| [actions/upload-artifact](https://github.com/actions/upload-artifact) | v7.0.1 | 24 |
| [aws-actions/amazon-ecr-login](https://github.com/aws-actions/amazon-ecr-login) | v2.1.6 | 1 |
| [aws-actions/configure-aws-credentials](https://github.com/aws-actions/configure-aws-credentials) | v6.2.3 | 1 |
| [bbusse/container-extract](https://github.com/bbusse/container-extract) | v1 | 4 |
| [docker/build-push-action](https://github.com/docker/build-push-action) | v7.3.0 | 2 |
| [docker/setup-buildx-action](https://github.com/docker/setup-buildx-action) | v4.2.0 | 2 |
| [docker/setup-qemu-action](https://github.com/docker/setup-qemu-action) | v4.2.0 | 1 |
| [vmactions/freebsd-vm](https://github.com/vmactions/freebsd-vm) | v1.5.2 | 4 |
