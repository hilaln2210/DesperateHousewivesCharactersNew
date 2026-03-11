# Desperate Housewives Character Guide

An Android app that provides an interactive character guide for the TV series *Desperate Housewives*. Browse and search all main characters with photos and detailed bios, with a polished splash/title screen on launch.

## Screenshots

> Screenshots available after running on an Android emulator or physical device.

## Features

- **Splash / Title Screen** — "DH" branding displayed for 3 seconds before transitioning to the character list
- **Character List** — Scrollable RecyclerView showing all main characters with their photo, name, and short description
- **Remote Image Loading** — Character photos fetched from URLs via the Coil library with crossfade animation, placeholder, and error fallback
- **Live Search** — `OutlinedTextField` filters characters in real time by name or description (case-insensitive)
- **Character Detail Dialog** — Tap any character to open a modal card dialog showing the full name and description
- **Compose + View interop** — Jetpack Compose hosts the app shell and dialogs; a classic `RecyclerView` adapter handles the scrollable list

### Characters included

Susan Mayer, Lynette Scavo, Bree Van de Kamp, Gabrielle Solis, Edie Britt, Mary Alice Young, Carlos Solis, Mike Delfino, Tom Scavo, Paul Young

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Kotlin |
| UI | Jetpack Compose (Material 3) + AndroidView interop |
| List rendering | RecyclerView + custom `CharacterAdapter` |
| Image loading | Coil (`io.coil-kt`) |
| Architecture | Single-Activity, composable-driven navigation |
| Build system | Gradle with Kotlin DSL + Version Catalog |
| Min SDK | 24 |
| Target / Compile SDK | 34 |
| AGP | 8.6.0 |
| Kotlin | 1.9.0 |

## Project Structure

```
DesperateHousewivesCharactersNew/
├── app/
│   └── src/main/
│       ├── java/com/example/desperatehousewivescharacters/
│       │   ├── MainActivity.kt          # Entry point; TitleScreen, CharacterList, CharacterAdapter
│       │   └── ui/theme/               # Material 3 theme (Color, Type, Theme)
│       ├── res/
│       │   ├── layout/item_character.xml  # RecyclerView item layout
│       │   └── values/                    # colors.xml, strings.xml, themes.xml
│       └── AndroidManifest.xml
├── gradle/
│   ├── libs.versions.toml              # Centralized version catalog
│   └── wrapper/
├── settings.gradle.kts
└── build.gradle.kts
```

## How to Build

### Prerequisites

- Android Studio Hedgehog (2023.1.1) or newer
- Android SDK with API level 34 platform installed
- JDK 17+

### Steps

1. Clone the repository and open the `DesperateHousewivesCharactersNew` folder in Android Studio.
2. Let Gradle sync complete — all dependencies download automatically.
3. Connect an Android device (API 24+) or create an AVD in the emulator.
4. Click **Run > Run 'app'** or press `Shift+F10`.

### Command-line build

```bash
./gradlew assembleDebug
```

Output APK: `app/build/outputs/apk/debug/app-debug.apk`

## Permissions

`android.permission.INTERNET` is declared in `AndroidManifest.xml` to allow loading character images from Wikipedia and other CDNs.
