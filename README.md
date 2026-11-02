# ZEGOCLOUD Live Streaming App

A Flutter live-streaming app built on [ZEGOCLOUD's prebuilt Live Streaming UIKit](https://www.zegocloud.com/docs/uikit/live-streaming-kit-flutter/overview) with [Clerk](https://clerk.com) for sign-in. Signed-in users can start a live stream as the host or join one as a viewer by entering its live ID.

## Features

- **Sign in / sign up / sign out** with Clerk's prebuilt UI.
- **Home**: greets you by username and offers *Start a live* or *Watch a live*.
- **Enter Live ID**: type the stream's ID, then *Start* (host) or *Watch* (audience).
- **Live page**: `ZegoUIKitPrebuiltLiveStreaming` with the host or audience config; your Clerk user ID and username identify you in the stream.

## How it works

```
lib/
├── main.dart                         # loads .env, ClerkAuth, provides UserCubit
├── data/config/env_config.dart       # reads ZEGO_APP_ID, ZEGO_APP_SIGN, CLERK_KEY
└── presentation/
    ├── login_page.dart
    ├── home_page.dart                # start / watch choice
    ├── enter_live_id_page.dart       # live ID entry
    ├── live_page.dart                # ZegoUIKitPrebuiltLiveStreaming
    └── cubits/user/user_cubit.dart   # holds the signed-in Clerk user
```

## Tech stack

- Flutter, Dart `>=3.2.6 <4.0.0`
- `zego_uikit_prebuilt_live_streaming` 3.3
- `clerk_flutter` (beta), `flutter_bloc`, `flutter_dotenv`, `gap`

## Getting started

### Environment variables

Create a `.env` file in the project root (bundled as an asset, not committed):

```
ZEGO_APP_ID="<your ZEGOCLOUD app ID>"
ZEGO_APP_SIGN="<your ZEGOCLOUD app sign>"
CLERK_KEY="<your Clerk publishable key>"
```

### Run

```sh
flutter pub get
flutter run
```

Streaming needs camera and microphone permissions, so use a real device or a desktop with a webcam. Start a live on one device and watch it from another with the same live ID.
