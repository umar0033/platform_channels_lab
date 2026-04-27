# Platform Channels Lab

Flutter lab project demonstrating two-way communication between Dart and native Android code using MethodChannel.

## Overview

This project fetches the device battery percentage from Android native APIs and displays it in a Flutter UI.

It is a practical example of:

- Calling platform-specific code from Flutter
- Returning native values back to Dart
- Handling success and error responses over a channel

## Team

- Mustafa Shahzad (22k-4166)
- Muhammad Umar Farooq (22k-4218)
- Syed Muhammad Abu Bakar (22k-4184)

## Features

- Flutter UI with a single action button: Get Battery Level
- MethodChannel bridge named samples.flutter.dev/battery
- Native Android battery retrieval with API-level compatibility logic
- User-friendly success and failure messages in the app

## How It Works

1. Flutter invokes getBatteryLevel using MethodChannel.
2. Android listens on the same channel in MainActivity.
3. Native Kotlin code reads battery percentage:
	 - API 21+: BatteryManager.BATTERY_PROPERTY_CAPACITY
	 - Older APIs: ACTION_BATTERY_CHANGED fallback
4. Result is returned to Flutter and rendered in the UI.

## Tech Stack

- Flutter
- Dart
- Kotlin (Android)
- MethodChannel API (platform channels)

## Project Structure

```text
platform_channels_lab/
|- lib/
|  |- main.dart                    # Flutter UI + MethodChannel call
|- android/
|  |- app/src/main/kotlin/com/example/platform_channels_lab/
|     |- MainActivity.kt           # Native Android MethodChannel handler
|- ios/
|- macos/
|- linux/
|- windows/
|- web/
|- pubspec.yaml
```

## Prerequisites

Make sure you have:

- Flutter SDK installed
- Android Studio or VS Code with Flutter/Dart extensions
- Android SDK and emulator (or physical Android device)

Check your setup:

```bash
flutter doctor
```

## Run Locally

1. Clone the repository

```bash
git clone <your-repo-url>
cd platform_channels_lab
```

2. Install dependencies

```bash
flutter pub get
```

3. Run on Android

```bash
flutter run
```

## MethodChannel Contract

- Channel name: samples.flutter.dev/battery
- Method: getBatteryLevel
- Return type: int (battery percentage)
- Error code: UNAVAILABLE

## Platform Support

- Fully implemented: Android (native battery reading through Kotlin)
- Flutter app scaffolding exists for iOS, macOS, Linux, Windows, and Web

## Learning Objectives

This lab helps you understand:

- When to use platform channels in Flutter
- How to design native method handlers
- How to keep platform-specific logic isolated while preserving a clean Flutter UI layer

## Troubleshooting

- No device detected:
	- Run flutter devices
	- Start an emulator or connect a phone with USB debugging enabled
- Build issues:
	- Run flutter clean
	- Then run flutter pub get and flutter run again
- Battery result unavailable:
	- Test on a real Android device if emulator behavior is inconsistent

## Future Improvements

- Add iOS battery implementation with Swift
- Add unit and integration tests for channel behavior
- Improve UI styling and state handling (loading/error indicators)

## License

This project is for educational and laboratory use.
