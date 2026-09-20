# 0.1.17-share-download — Verification

| Field | Value |
|---|---|
| File | `Mgboard-Android-0.1.17-share-download.apk` |
| Size | 209,483 bytes |
| SHA-256 | `7cacb1e14631e8b7961515daf59b13bec897ca0eca895dbb1ca5c40c4fad3f5b` |
| versionCode / versionName | 22 / `0.1.17-share-download` |
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
- Browser/native-mock regression suite + नया `share-link` guard: full `npm test` **1013 checks PASS**। share-link guard verify करता है कि Share text में सिर्फ public download link हो और private source link न हो।
- `classes.dex` / `classes2.dex` 0.1.16 से **byte-identical** — native editor code unchanged।
- Frozen `web-source/index.html` SHA-256 unchanged: `01b888852ff59d2461cf54479e9e2c747a1b6ba4f543b6d2fc4058e187d98731`।

**Scope**: यह local verification है — production signing, Play compatibility और real-device InputConnection E2E की गारंटी नहीं।
