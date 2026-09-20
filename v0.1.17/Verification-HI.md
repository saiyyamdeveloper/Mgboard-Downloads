# 0.1.17-share-download — Verification

| Field | Value |
|---|---|
| File | `Mgboard-Android-0.1.17-share-download.apk` |
| Size | 212,195 bytes |
| SHA-256 | `df0ead30d9d52b0e147e8ff03b683a6e57e9fda8f1051fcf16811d868d9fe7bc` |
| versionCode / versionName | 20 / `0.1.17-share-download` |
| Package | `io.github.saiyyamdeveloper.mgboard.android` |
| minSdk / targetSdk | 26 / 35 |
| Signing | Android Debug key, v2+v3 scheme verified (v1 off) |
| zipalign | 4-byte aligned, verified |

## Checksum verify

```sh
sha256sum -c Mgboard-Android-0.1.17-share-download.apk.sha256
```

## Build evidence (builder machine)

- Gradle `:app:assembleDebug :app:testDebugUnitTest :app:lintDebug` — **BUILD SUCCESSFUL** (AGP 8.7.3, JDK 21, SDK 35)।
- Java unit tests: **96/96 PASS**।
- Lint: 0 errors, 1 pre-existing `SetJavaScriptEnabled` warning।
- Browser/native-mock regression suite + नया `share-link` guard: full `npm test` पास।
- `classes.dex` / `classes2.dex` 0.1.16 से **byte-identical** — native editor code unchanged।
- Frozen `web-source/index.html` SHA-256 unchanged: `01b888852ff59d2461cf54479e9e2c747a1b6ba4f543b6d2fc4058e187d98731`।
- इस build का change सिर्फ `android-adapter.js` (share text), `NOTICE`, `build.gradle` version और packaged assets है।

**Scope**: यह local verification है — production signing, Play compatibility और real-device InputConnection E2E की गारंटी नहीं।
