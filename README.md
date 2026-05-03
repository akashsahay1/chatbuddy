# Chat Buddy

A Flutter chat application that lets you converse with a bot through both text and voice. It uses on-device speech recognition for input and text-to-speech for replies, providing a hands-free conversational experience.

## Features

- Text-based chat with a simple rule-based bot
- Voice input via on-device speech-to-text
- Spoken bot responses via text-to-speech
- Auto-scroll to the latest message
- Clear-chat action in the app bar
- Cross-platform: Android, iOS, Web, macOS, Linux, Windows

## Tech Stack

- **Framework:** Flutter (Dart SDK ^3.6.1)
- **Speech recognition:** [`speech_to_text`](https://pub.dev/packages/speech_to_text) ^7.0.0
- **Text-to-speech:** [`flutter_tts`](https://pub.dev/packages/flutter_tts) ^4.2.2
- **HTTP client:** [`http`](https://pub.dev/packages/http) ^1.3.0 (reserved for future API integration)

## Project Structure

```
chatbuddy/
├── lib/
│   └── main.dart          # App entry point and chat UI
├── android/               # Android platform code
├── ios/                   # iOS platform code
├── web/                   # Web platform code
├── macos/ linux/ windows/ # Desktop platform code
├── pubspec.yaml           # Dependencies and Flutter config
└── README.md
```

## Getting Started

### Prerequisites

- [Flutter SDK](https://docs.flutter.dev/get-started/install) (3.6.1 or newer)
- A configured target platform (Android Studio / Xcode / Chrome / desktop toolchain)

### Install

```bash
git clone https://github.com/akashsahay1/chatbuddy.git
cd chatbuddy
flutter pub get
```

### Run

```bash
flutter run
```

To target a specific device, list available devices first:

```bash
flutter devices
flutter run -d <device-id>
```

### Build

```bash
flutter build apk        # Android
flutter build ios        # iOS
flutter build web        # Web
flutter build macos      # macOS
```

## Permissions

Voice input requires microphone (and on iOS, speech recognition) permissions. These are configured per platform:

- **Android:** `RECORD_AUDIO` in `android/app/src/main/AndroidManifest.xml`
- **iOS:** `NSMicrophoneUsageDescription` and `NSSpeechRecognitionUsageDescription` in `ios/Runner/Info.plist`

## How It Works

The bot logic lives in `_getAIResponse` in `lib/main.dart` and matches keywords (`hello`, `how are you`, `weather`, `thank you`) to canned replies. It is intentionally simple — the `http` dependency is in place so the response source can later be swapped for a trained-model API or another LLM backend.

## Roadmap

- Wire up an external AI/LLM API in place of the rule-based responder
- Persist chat history across sessions
- Multi-language support for STT and TTS
- Theming (light/dark) and message timestamps

## License

This project is provided as-is for learning and personal use. Add a license file before distribution.
