# Agent guide

This repo holds small Dart and Flutter packages that anyone can use.

## Direction

- Keep packages small and dependency-light.
- Keep public APIs stable. A breaking change needs a CHANGELOG note that says what callers must now pass.
- Packages hold no app-specific values. Project ids, API keys, URLs, client ids, URL schemes and bundle ids are parameters the caller passes. Tests and examples use neutral values such as `example-project` and `user@example.com`.
- Each package versions and tags independently as `<name>-vX.Y.Z`.

## Releasing a package

A release touches one package only.

1. In one PR, bump that package's `pubspec.yaml` version and its `CHANGELOG.md`.
2. After the merge, tag the merge commit `<name>-vX.Y.Z`.
3. Never use a repo-wide tag like `vX.Y.Z`. Anything keyed off tags filters on `<name>-v*`.

## Glossary

- Package: one directory under `packages/` with its own `pubspec.yaml`, README, CHANGELOG, LICENSE and tests.
- Pure-Dart package: runs on the plain Dart SDK. Checked locally with `dart`.
- Plugin: a Flutter package with native Apple code (`darwin/`) and an `example/` app. Checked by CI only.
- Package tag: `<name>-vX.Y.Z`, the version a git dependency pins with `ref:`.

## Workflow

- Packages are independent. A pub workspace was not used because the pure-Dart packages and the Flutter plugins resolve with different SDKs.
- Changes land through a PR.
