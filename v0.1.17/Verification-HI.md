# 0.1.17-space-scrub — Verification

| Field | Value |
|---|---|
| File (release asset) | `Mgboard-Android-latest.apk` (stable name — yahi direct link se download hoti hai) |
| Size | 213,869 bytes |
| SHA-256 | `dc84b312955c3e3bb2312fbf4e43962e65faf3908c1e97af725e9e17715e7d23` |
| versionCode / versionName | 26 / `0.1.17-space-scrub` |
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
- Browser/native-mock regression suite + `share-link` + `toolbar-x` + `customize-panel` + **naya `space-scrub` guard**: full `npm test` **1025 checks PASS** (exit 0)।
  - `space-scrub` guard verify करता है: tap = exactly one space; slow horizontal drag = exact grapheme steps with no space inserted; vertical slip = tap (space) नहीं scrub; fast flick = velocity factor (baseline से तेज़, text की start tak); Devanagari "किताब" में cluster edges (5→4→2→0, mid-cluster नहीं); ZWJ emoji family = single grapheme (UTF-16 edge पर landing); दोनों boundaries par clamp; `‹ ›` visual cue sirf drag के dauran; CDP two-finger touch se second-finger ghost-tap lockout (doosri key commit नहीं)।
  - `customize-panel` guard: pencil/customize mode = exactly 1 panel, saare options ek single-column list (top-to-bottom, vertical scroll), dots gayab; pin/unpin chupchaap (popup नहीं, state sahi update); max-pin warning still visible; pencil off/normal mode = 2-column paginated grid wapas।
  - `toolbar-x` guard: popup band = 4-dot grid; open = circular grey ✕; customise = ✓; close = grid restore; duplicate header-✕ row छिपा।
  - `share-link` guard: सिर्फ direct latest-download URL (stable asset name), private source link नहीं।
- `classes.dex` 0.1.16 से **byte-identical** — native editor code unchanged।
- Frozen `web-source/index.html` SHA-256 unchanged: `01b888852ff59d2461cf54479e9e2c747a1b6ba4f543b6d2fc4058e187d98731` — typing engine/layout अछूता।

**नया change कहाँ है**: सिर्फ Android-only bridge `assets/android-adapter.js` में — spacebar का frozen `attachSpaceDrag` global override (slop gate + direction bias, velocity-scaled delta accumulator, grapheme-edge stepping with `Intl.Segmenter` + app-constants fallback, per-step haptic ticks, `‹ ›` cue, second-finger lockout); native cursor sync existing `teSetCursor`→`apply`→`setSelection` transactional pipeline se hi। Web source, key tables, IME algorithms, native Java — सब byte-identical।

**Scope**: यह local verification है — production signing, Play compatibility और real-device InputConnection/vibration/two-finger E2E की गारंटी नहीं।
