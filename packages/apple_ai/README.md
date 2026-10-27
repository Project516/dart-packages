# apple_ai

Apple's on-device foundation model (Apple Intelligence) as one text-in /
text-out call.

```dart
final availability = await appleAiAvailability();
if (availability.isAvailable) {
  final answer = await appleAiRespond(
    prompt: 'Which of these teams climbs most reliably?',
    instructions: 'Answer in two sentences.',
  );
}
```

The model ships with the OS: nothing is downloaded, nothing leaves the device,
there is no key and no request budget. That makes it a good offline fallback
and a bad primary, because it is a small model and it is only there on some
devices.

## Things worth knowing before using it

- **Ask `appleAiAvailability()` first, every time.** The answer changes over
  the life of an install: Apple Intelligence is a Settings toggle and the
  model downloads in the background. `AppleAiUnavailableReason` separates the
  four cases because they need different things from a person, and each one
  carries a `message` fit to show.
- **It needs iOS 26 / macOS 26 and hardware that supports Apple
  Intelligence.** Everywhere else, including Android, Windows, Linux and the
  web, availability answers `unsupportedOs` without touching the channel.
- **A call without `sessionId` has no memory.** Pass the same `sessionId` to
  continue a conversation, and call `appleAiCloseSession` to end it.
  `instructions` and `tools` apply when a session starts, so changing either
  needs a new `sessionId`.
- **Tools run in Dart.** Pass `tools` (each an `AppleAiTool` with a JSON
  Schema for its arguments) and set one handler at startup with
  `appleAiSetToolHandler`. Without a handler the model asks for tools nothing
  answers.
- **The model has its own guardrails.** A prompt it declines comes back as an
  `AppleAiException`, not as text, so treat a failure as "no answer" rather
  than an error worth showing as a broken screen.
