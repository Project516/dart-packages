## Unreleased

- The method channel is now named `dev.project516.apple_web_auth` (the
  previous name was team-specific). Migration: nothing to pass when calling
  `appleWebAuthenticate()`. `callbackScheme` has no default; the caller passes
  the URL scheme registered in its own app. Tests that mock the channel by name
  must use the new name.
- Example app bundle ids are now `dev.project516.appleWebAuthExample`.

## 0.0.2

- Corrected the package `LICENSE` from MIT to AGPL-3.0, matching the repo.

## 0.0.1

- Initial `appleWebAuthenticate()` over `ASWebAuthenticationSession`, so an
  OAuth flow can redirect to a registered URL scheme instead of a loopback
  web server.
