# Mgboard-Downloads — मैसरम गोंडी कीबोर्ड APK

यह repository केवल **Mgboard Android keyboard** के आधिकारिक downloadable APK का public archive है। सॉर्स कोड अलग (private) repository `saiyyamdeveloper/Mgboard` में है और इस repository में source नहीं शामिल है।

## नवीनतम version

| Field | Value |
|---|---|
| Version | **0.1.17-share-download** (versionCode 21) |
| Package | `io.github.saiyyamdeveloper.mgboard.android` |
| Android | 8.0 (API 26)+, WebView-based |
| नया feature | scored suggestions (top 3) + guarded auto-space + **Share बटन में सीधा download link + source link** |
| Install | [Latest release](https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest) से APK डाउनलोड करें |

## Install कैसे करें

1. [Latest release](https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest) खोलें और APK download करें।
2. फ़ोन पर "Unknown sources" (अनजान स्रोत) की अनुमति दें — installer पॉपअप में ही option मिलेगा।
3. APK install करें। पहले से Mgboard लगा हो तो **Update** चुनें (uninstall की ज़रूरत नहीं, data रह जाएगा)।
4. Settings → Language & Input में Mgboard active करके select करें।

## Share link क्यों बनाया गया

पहले कीबोर्ड के Share बटन में सिर्फ GitHub profile का link था, जिससे दूसरे को APK download नहीं मिल पा रहा था। अब Share text में यह permanent links जाते हैं:

```
https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest
GitHub (source): https://github.com/saiyyamdeveloper/Mgboard
```

इसलिए जो भी नया version publish होता है, Share वाला download link अपने-आप उसी नए version पर ले जाता है — पुराना link कभी "भ्रामक पुराना" नहीं रहता। Source repository अभी private है, इसलिए source link केवल reference है; download link हमेशा public रहेगा।

## Checksum verify करना (optional but recommended)

हर release में APK के साथ `.sha256` file होती है। Terminal/PC पर:

```sh
sha256sum -c Mgboard-Android-0.1.17-share-download.apk.sha256
```

`OK` दिखे तो file असली है।

## Version history

### 0.1.17-share-download (versionCode 21) — 2026-09-20
- Share बटन अब public download page (यही repository) + `Mgboard` source link share करता है — receiver सीधे नया version install कर सकता है।
- Scored suggestions: 784 English + 844 Hindi + 624 Hinglish offline words, 168 curated bigram pairs, config-based weights (`w_lm=2.0`, `w_edit=1.5`, `w_freq=0.35`)।
- Guarded auto-space: suggestion accept पर एक space, अगली punctuation अपने-आप space हटाती है, duplicate space नहीं, Enter trailing auto-space हटाकर newline/Send रखता है।
- Keyboard की height और key layout unchanged; native DEX 0.1.16 से byte-identical।
- 1013 automated checks (browser/native mock + Java unit) पास; real-phone E2E बाकी।

### 0.1.16-preview (versionCode 18) — 2026-09-19
- भाषा-change popup suppression, barakhadi conjunct forms, geometry fixes। (Private Mgboard repository पर available)

## Privacy

- कीबोर्ड typing local रहती है; कोई cloud sync/telemetry नहीं।
- Suggestions पूरी तरह offline curated data से आते हैं — कोई trained Gboard model, कोई observed user frequency, कोई network call नहीं।
- Voice input (optional) के लिए RECORD_AUDIO permission सिर्फ user accept करने के बाद माँगी जाती है।

## Signing note

यह APK **debug signing key** से signed है (preview/testing distribution)। इसे production Play-Ready signing नहीं मानें। Same package पर update के लिए हमेशा इसी repository का नया version use करें।
