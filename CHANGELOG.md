# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.0.14] - 2026-10-12

### Internal

- Add linters to CI. Lint code.

## [0.0.13] - 2026-10-12

### Internal

- Update dependencies.

## [0.0.12] - 2026-05-15

### Internal

- Add explicit workflow permissions.

## [0.0.11] - 2026-05-15

### Internal

- Bumped `joshjohanning/ensure-immutable-actions` from `v2.5.3` to `v2.5.4`.

## [0.0.10] - 2026-04-21

### Changed

- Hardened CI by adding a test-suite check that rejects mutable GitHub Action references in workflows.

## [0.0.9] - 2026-04-21

### Changed

- Hardened CI by adding a test-suite check that rejects mutable GitHub Action references in workflows.

## [0.0.8] - 2026-04-20

### Changed

- Hardened CI by adding a test-suite check that rejects mutable GitHub Action references in workflows.

## [0.0.7] - 2026-03-2

### Fixed

- Switched release README tag verification from `rg -P` to `grep -P`.

## [0.0.6] - 2026-03-26

No code changes from `0.0.4`. Released to restore the latest published version after deleting `0.0.5`.

## [0.0.4] - 2026-03-26

### Changed

- Renamed the action metadata title to `Setup Docker Desktop macOS` to fix listing on Marketplace.
- Added Marketplace branding with the `download-cloud` icon and blue color.

### Fixed

- Updated `change-validation.yml` to use the checked-out local action instead of `main`.

## [0.0.2] - 2026-03-25

### Changed

- Inlined the hosted macOS validation job into `change-validation.yml` to remove an extra workflow layer.
- Removed redundant example and end-to-end workflows to keep the repository leaner.

## [0.0.1] - 2026-03-25

### Added

- Initial public release of the `setup-docker-desktop-macos` action.
- A composite GitHub Action that installs and starts Docker Desktop on macOS runners.
- Validation workflows covering `macos-15-intel` and `macos-26-intel`.
- Release validation that tests the tagged action before creating the GitHub release.
- User documentation describing usage, supported runners, Docker Desktop license responsibility,
  and the `id-token: write` limitation on GitHub-hosted macOS runners.

### Changed

- Reduced workflow token permissions to avoid a GitHub-hosted macOS startup issue when `id-token: write`
  is granted.
