# Userly

An offline handle/username finder. It generates and filters candidate handles, tracks which ones
you've already tried, and records the ones you've claimed — no account, no network, no tracking.

**Live site: <https://penguino-o.github.io/userly/>**

## Download (Android)

- [userly-release.apk](https://penguino-o.github.io/userly/userly-release.apk) — signed release build
- [userly.apk](https://penguino-o.github.io/userly/userly.apk) — debug build

Release APK SHA-256: `9f12eb6b92d498273cc45b18684d14fde3c631aba5bf0f64a31efbe840f5529f`

## What it does

- **Combination generator** — builds handles from your own word/separator/number patterns, filtered
  by length and allowed characters.
- **English word generator** — 8,623 built-in English words as a seed list.
- **Click to copy** any suggestion to the clipboard.
- **Tried lists per length** — mark a handle as taken so it stops surfacing, per length bucket.
- **Claimed records** — keep the handles you actually registered.
- Everything runs in the page. Nothing leaves your device; state is kept in local storage.

## Repo layout

```
index.html                 the entire web app (single file, word list embedded)
android/                   Gradle wrapper app: WebView + native clipboard bridge
userly-release.apk         signed release APK (also served by the live site)
userly-release.aab         Play Store bundle
userly.apk                 debug APK
```

## Building the Android app

```bash
cd android
./gradlew assembleRelease     # or bundleRelease for the .aab
```

Signing needs a `keystore.properties` next to `android/settings.gradle`:

```properties
storeFile=../keystore/userly-release.jks
storePassword=...
keyAlias=userly
keyPassword=...
```

`keystore.properties`, the keystore directory and all build output are gitignored — this repo
contains no signing secrets. To build from source you supply your own key.

## Hosting

The site is served straight from `main` via GitHub Pages (`index.html` at the repo root), so any
push to `main` republishes it.
