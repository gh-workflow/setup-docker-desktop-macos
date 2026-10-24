# setup-docker-desktop-macos

[![Release](https://img.shields.io/github/v/release/gh-workflow/setup-docker-desktop-macos?style=flat-square)](https://github.com/gh-workflow/setup-docker-desktop-macos/releases)
[![Immutable Releases](https://img.shields.io/badge/releases-immutable-blue?labelColor=333)](https://docs.github.com/en/code-security/supply-chain-security/understanding-your-software-supply-chain/immutable-releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-setup--docker--desktop--macos-blue?logo=github&labelColor=333&style=flat-square)](https://github.com/marketplace/actions/setup-docker-desktop-macos)
[![Tests](https://img.shields.io/github/actions/workflow/status/gh-workflow/setup-docker-desktop-macos/change-validation.yml?branch=main&label=test&style=flat-square)](https://github.com/gh-workflow/setup-docker-desktop-macos/actions/workflows/change-validation.yml)
[![macOS](https://img.shields.io/badge/platform-macOS-000000?logo=apple&logoColor=white&style=flat-square)](#supported-runners)
[![Docker Desktop](https://img.shields.io/badge/docker-desktop-2496ED?logo=docker&logoColor=white&style=flat-square)](https://www.docker.com/products/docker-desktop/)

Install and start Docker Desktop on macOS GitHub Actions runners.

Use this when you need Docker Desktop on macOS to test workflows or applications that depend on Docker there.

Do not use this to build and publish Linux images. Use Linux runners for that.

## Usage

```yaml
name: ci

on:
  push:

jobs:
  docker:
    runs-on: macos-26-intel
    steps:
      - name: Checkout
        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd  # v6.0.2

      - name: Setup Docker Desktop macOS
        uses: gh-workflow/setup-docker-desktop-macos@0.0.15
        with:
          print_diagnostics: false

      - name: Validate Docker
        run: docker run --rm hello-world
```

## Inputs

| Name                | Required | Description                                                             |
|---------------------|----------|-------------------------------------------------------------------------|
| `print_diagnostics` | no       | Print Docker CLI and install diagnostics after Docker Desktop is ready. |

## Supported runners

- GitHub-hosted Intel macOS runners:
  - `macos-15-intel`
  - `macos-26-intel`
- Self-hosted Intel macOS runners
- Self-hosted arm64 macOS runners

GitHub-hosted macOS arm64 runners are unsupported because GitHub does not support [nested virtualization](https://docs.github.com/en/actions/reference/runners/github-hosted-runners#limitations-for-arm64-macos-runners)
on them.

## Permission caveat

On GitHub-hosted macOS runners, this action does not work in jobs that grant `id-token: write`.
In those jobs, Docker Desktop does not finish startup and `docker.sock` never appears.

Workaround: call this action from a job or reusable workflow that does not grant `id-token: write`.

## License note

This action runs Docker Desktop's installer with `--accept-license --user="$USER"`. You are responsible for
complying with Docker's license and subscription terms.
