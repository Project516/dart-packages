# dart-packages

Small Dart and Flutter packages, each versioned and tagged on its own.

| Package | Version | What it is |
| --- | --- | --- |
| [tba_client](packages/tba_client) | 0.9.0 | The Blue Alliance API v3 client, pure Dart. |
| [statbotics_client](packages/statbotics_client) | 0.4.0 | Statbotics API client, pure Dart. |
| [match13_client](packages/match13_client) | 0.2.0 | match13 API client, pure Dart. |
| [firestore_client](packages/firestore_client) | 0.6.0 | Firebase Auth and Firestore over REST, pure Dart. |
| [liquid_glass](packages/liquid_glass) | 0.7.0 | Apple Liquid Glass as a Flutter platform view (iOS and macOS). |
| [apple_ai](packages/apple_ai) | 0.1.1 | Apple on-device Foundation Models for Flutter (iOS and macOS). |
| [apple_web_auth](packages/apple_web_auth) | 0.0.2 | `ASWebAuthenticationSession` for Flutter (iOS and macOS). |

## Use a package

The packages are not on pub.dev yet. Depend on one by git, pinned to its tag:

```yaml
dependencies:
  tba_client:
    git:
      url: https://github.com/Project516/dart-packages
      path: packages/tba_client
      ref: tba_client-v0.9.0
```

## Development

Each package is independent and has its own `pubspec.yaml`. From a package directory:

```sh
dart pub get   # flutter pub get for the Apple plugins
dart format .
dart analyze --fatal-infos
dart test      # flutter test for the Apple plugins
```

CI runs the same checks for every package, plus iOS and macOS builds of the plugin example apps.

## License

AGPL-3.0-only. See [LICENSE](LICENSE). Each package also carries its own copy.
