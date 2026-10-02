## Unreleased

- The method channel `appleAiChannel` is now named `dev.project516.apple_ai`
  (the previous name
  was team-specific). Migration: nothing to pass when using the
  package functions. Tests that mock the channel by name must use the new name.
- Example app bundle ids are now `dev.project516.appleAiExample`.

## 0.1.1

- Corrected the package `LICENSE` from MIT to AGPL-3.0, matching the repo.

## 0.1.0

- Tool calling: `appleAiRespond` takes `tools`, and `appleAiSetToolHandler`
  runs them in Dart. A tool's JSON Schema becomes a `DynamicGenerationSchema`
  at runtime, so a registry assembled in Dart works without a compile-time
  `@Generable` Swift type.
- Multi-turn conversations: pass a `sessionId` to keep a session and its
  transcript alive between calls, and `appleAiCloseSession` to end it.

## 0.0.1

- Initial `appleAiAvailability()` / `appleAiRespond()` over Apple's on-device
  foundation model (FoundationModels), on iOS 26 and macOS 26, unavailable
  everywhere else rather than broken.
