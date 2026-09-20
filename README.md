# Mgboard-Downloads — मैसरम गोंडी कीबोर्ड APK

यह repository केवल **Mgboard Android keyboard** के आधिकारिक downloadable APK का public archive है।

## नवीनतम version

| Field | Value |
|---|---|
| Version | **0.1.17-space-scrub** (versionCode 26) |
| Package | `io.github.saiyyamdeveloper.mgboard.android` |
| Android | 8.0 (API 26)+, WebView-based |
| नया feature | **Gboard-style spacebar cursor scrubbing** (tap = space, horizontal drag = cursor scrub: velocity-scaled steps, grapheme-safe, haptic ticks, `‹ ›` cue, ghost-tap lockout) + Customize panel single-column + silent pin/unpin + Gboard-style toolbar close button (✕/✓) + scored suggestions (top 3) + guarded auto-space + **Share बटन में direct download link** |
| Direct download | [Mgboard-Android-latest.apk](https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest/download/Mgboard-Android-latest.apk) (click → seedha download start) |
| Release page | [Latest release](https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest) |

## Install कैसे करें

1. Keyboard से Share किया गया **direct link** click करें — APK download तुरंत start हो जाता है। (या [release page](https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest) से APK select करें।)
2. Download complete होने पर file पर tap करें।
3. फ़ोन पर "Unknown sources" (अनजान स्रोत) की अनुमति दें — installer पॉपअप में ही option मिलेगा।
4. Install करें। पहले से Mgboard लगा हो तो **Update** चुनें (uninstall की ज़रूरत नहीं, data रह जाएगा)।
5. Settings → Language & Input में Mgboard active करके select करें।

## Share link कैसे काम करता है

पहले कीबोर्ड के Share बटन में सिर्फ GitHub profile का link था, जिससे दूसरे को APK download नहीं मिल पा रहा था। अब Share text में यह **direct download link** जाता है:

```
https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest/download/Mgboard-Android-latest.apk
```

इस link को click करते ही **seedha APK download start** हो जाता है — बीच में कोई page नहीं। `latest` isliye use hota hai kyunki jo bhi naya version publish hota hai, **wahi shared link apne-aap naya APK de deta hai**।

**Stable asset name convention:** har future release mein APK ka file name `Mgboard-Android-latest.apk` hi rehta hai, taaki yeh direct link hamesha valid rahe। Version ka number release tag/notes mein hota hai.

## Checksum verify करना (optional but recommended)

हर release में APK के साथ `.sha256` file होती है। Terminal/PC पर:

```sh
sha256sum -c Mgboard-Android-latest.apk.sha256
```

`OK` दिखे तो file असली है।

## Version history

### 0.1.17-space-scrub (versionCode 26) — 2026-09-20
- **Gboard-style spacebar dual-mode**: tap = space (unchanged); horizontal drag = text cursor scrub।
- Scrub activation: slop gate (8px) + direction bias (|dx| > 1.25·|dy|) — vertical slip par tap hi rehta hai।
- Physics: velocity-scaled delta accumulator (baseline 12px/step, fast flick par 2.2× tak), per-event step cap।
- Grapheme-safe cursor stepping (Devanagari matra, Masaram Gondi matra/virama, ZWJ emoji, flags, skin tones) — consonant ke beech matra nahi todti।
- Har step par haptic tick (boundary par suppress); scrub ke dauran spacebar par `‹ ›` chevron + subtle darkening; second-finger ghost-tap lockout।
- Scrub ke baad release par koi space nahi। Native cursor sync existing transactional `apply`→`setSelection` pipeline se — koi Java change nahi।
- Customize single-column + silent pin/unpin + toolbar ✕/✓ + direct download link unchanged; native DEX 0.1.16 se byte-identical।
- 1025 automated checks (browser/native mock + Java unit) पास; real-phone E2E बाकी।

### 0.1.17-toolbar-v2 (versionCode 25) — 2026-09-20
- **Customize mode (pencil) single-column panel**: saare options ek hi jagah, ek column mein, upar se neeche; left-right page-slide aur dots hata; panel vertical scroll।
- **Pin/unpin silent**: drag-drop se pin/unpin chupke se (item visibly move); "pin ho gaya/unpin ho gaya" popup nahi; max-pin warning still।
- Normal toolbar popup unchanged (2-column grid + pages); toolbar close affordance (✕/✓) unchanged।
- Direct download share link unchanged; native DEX 0.1.16 se byte-identical।
- 1016 automated checks (browser/native mock + Java unit) पास; real-phone E2E बाकी।

### 0.1.17-toolbar-x (versionCode 24) — 2026-09-20
- **Gboard-style toolbar close button**: tools popup open hote hi top-left ka 4-dot grid **circular grey button + light ✕** ban jaata hai (tap par popup band)।
- **Customize mode (pencil)** mein wahi jagah **✓** — tap par customize confirm।
- Popup ka purana alag header row (duplicate ✕) hat gaya — tools ab seedhe toolbar row ke neeche dikhte hain (Gboard reference layout)।
- Popup band hone par 4-dot grid bilkul waisa hi hai — wahi popup kholta hai।
- Direct download share link unchanged; native DEX 0.1.16 se byte-identical।
- 1015 automated checks (browser/native mock + Java unit) पास; real-phone E2E बाकी।

### 0.1.17-share-download (versionCode 23) — 2026-09-20
- Share बटन अब **direct download link** देता है — receiver के phone पर link click करते ही APK download start (latest release से, stable asset name `Mgboard-Android-latest.apk`)।
- Scored suggestions: 784 English + 844 Hindi + 624 Hinglish offline words, 168 curated bigram pairs, config-based weights (`w_lm=2.0`, `w_edit=1.5`, `w_freq=0.35`)।
- Guarded auto-space: suggestion accept पर एक space, अगली punctuation अपने-आप space हटाती है, duplicate space नहीं, Enter trailing auto-space हटाकर newline/Send रखता है।
- Keyboard की height और key layout unchanged; native DEX 0.1.16 से byte-identical।
- 1013 automated checks (browser/native mock + Java unit) पास; real-phone E2E बाकी।

### 0.1.16-preview (versionCode 18) — 2026-09-19
- भाषा-change popup suppression, barakhadi conjunct forms, geometry fixes।

## Privacy

- कीबोर्ड typing local रहती है; कोई cloud sync/telemetry नहीं।
- Suggestions पूरी तरह offline curated data से आते हैं — कोई trained Gboard model, कोई observed user frequency, कोई network call नहीं।
- Voice input (optional) के लिए RECORD_AUDIO permission सिर्फ user accept करने के बाद माँगी जाती है।

## Signing note

यह APK **debug signing key** से signed है (preview/testing distribution)। इसे production Play-Ready signing नहीं मानें। Same package पर update के लिए हमेशा इसी repository का नया version use करें।
