# 0.1.17-share-download — Verification

| Field | Value |
|---|---|
| File (release asset) | `Mgboard-Android-latest.apk` (stable name — yahi direct link se download hoti hai) |
| Size | 209,504 bytes |
| SHA-256 | `f658a097ea17815b9c9ead86435b5bc9f82911ed0ef788dcba5dbdc25aefb191` |
| versionCode / versionName | 23 / `0.1.17-share-download` |
| Package | `io.github.saiyyamdeveloper.mgboard.android` |
| minSdk / targetSdk | 26 / 35 |
| Signing | Android Debug key, v2+v3 scheme verified (v1 off) |
| zipalign | 4-byte aligned, verified |

## Checksum verify

```sh
sha256sum -c Mgboard-Android-latest.apk.sha256
```

## Build evidence (builder machine)

- Gradle `:app:assembleDebug :app:testDebugUnitTest :app:lintDebug` — **BUILD SUCCESSFUL** (AGP 8.7.3, JDK 21, SDK 35)।
- Java unit tests: **96/96 PASS**।
- Lint: 0 errors, 1 pre-existing `SetJavaScriptEnabled` warning।
- Browser/native-mock regression suite + नया `share-link` guard: full `npm test` **1013 checks PASS**। share-link guard verify करता है कि Share text में सिर्फ direct latest-download URL (stable asset name) हो और private source link न हो।
- `classes.dex` / `classes2.dex` 0.1.16 से **byte-identical** — native editor code unchanged।
- Frozen `web-source/index.html` SHA-256 unchanged: `01b888852ff59d2461cf54479e9e2c747a1b6ba4f543b6d2fc4058e187d98731`।

**Scope**: यह local verification है — production signing, Play compatibility और real-device InputConnection E2E की गारंटी नहीं।
