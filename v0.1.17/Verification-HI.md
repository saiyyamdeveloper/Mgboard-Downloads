# 0.1.17-toolbar-x — Verification

| Field | Value |
|---|---|
| File (release asset) | `Mgboard-Android-latest.apk` (stable name — yahi direct link se download hoti hai) |
| Size | 210,486 bytes |
| SHA-256 | `a617ec8d473add455ba12393512bf19e47c243a9f23acb9ea4f34059d8759f4f` |
| versionCode / versionName | 24 / `0.1.17-toolbar-x` |
| Package | `io.github.saiyyamdeveloper.mgboard.android` |
| minSdk / targetSdk | 26 / 35 |
| Signing | Android Debug key, v2+v3 scheme verified (v1 off) |
| zipalign | 4-byte aligned, verified |

## Checksum verify

```sh
sha256sum -c Mgboard-Android-latest.apk.sha256
```

## Build evidence (builder machine)

- Gradle `:app:assembleDebug :app:testDebugUnitTest` — **BUILD SUCCESSFUL** (AGP 8.7.3, JDK 21, SDK 35)।
- Java unit tests: **96/96 PASS**।
- Browser/native-mock regression suite + `share-link` guard + **naya `toolbar-x` guard**: full `npm test` **1015 checks PASS** (exit 0)।
  - `toolbar-x` guard verify करता है: popup बंद = 4-dot grid वैसे का वैसे; popup खुला = circular grey ✕ (dots छिपे, blue नहीं); pencil/customize = ✕ की जगह ✓; ✓ tap पर popup बंद + grid restore; और popup का duplicate header-✕ row सभी states में छिपा।
  - `share-link` guard: Share text में सिर्फ direct latest-download URL (stable asset name) + private source link नहीं।
- `classes.dex` 0.1.16/v23 से **byte-identical** — native editor code unchanged।
- Frozen `web-source/index.html` SHA-256 unchanged: `01b888852ff59d2461cf54479e9e2c747a1b6ba4f543b6d2fc4058e187d98731` — typing engine/layout अछूता।

**नया change कहाँ है**: सिर्फ Android-only bridge `assets/android-adapter.js` में (runtime style + 2 SVG icons inject, MutationObserver sync)। Web source, key tables, IME algorithms, native Java — सब byte-identical।

**Scope**: यह local verification है — production signing, Play compatibility और real-device InputConnection E2E की गारंटी नहीं।
