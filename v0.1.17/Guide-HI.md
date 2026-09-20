# Mgboard 0.1.17-share-download — Install और Share Guide

## नया क्या है

1. **Share बटन में direct download link**: कीबोर्ड menu → Share पर अब सिर्फ यह text जाता है:

   ```
   Mgboard Android — मासरम गोंडी कीबोर्ड (0.1.17)
   नया version यहाँ से download करके install करें (direct download):
   https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest/download/Mgboard-Android-latest.apk
   ```

   Receiver यह link click करते ही **APK download seedha start** हो जाता है — बीच में कोई page नहीं। `latest` + stable asset name (`Mgboard-Android-latest.apk`) की वजह से अगला version publish होते ही वही link नया APK देगा।

   Install: download complete होने पर file पर tap करें → "Unknown sources" allow करें → install करें। (Android में install का tap सिस्टम security rule है — कोई app भी chupke se auto-install नहीं कर सकती।)

2. **Scored suggestions (top 3)**: current prefix + पिछले committed शब्द के bigram context से तीन candidates; weights बाहरी config से (`w_lm=2.0, w_edit=1.5, w_freq=0.35`)।
3. **Guarded auto-space**: suggestion accept → एक space; अगली punctuation (`. , ? ! ; : । ॥` आदि) उसी space को अपने-आप हटाकर punctuation लिखती है; पहले से मौजूदा space duplicate नहीं होती; Enter trailing auto-space हटाकर newline/Send रखता है।

## Quick test

| Type | Expected |
|---|---|
| `good mo` (QWERTY) | पहला suggestion **morning** |
| `send mo` | पहला suggestion **money** |
| `कल सु` (Hindi) | पहला suggestion **सुबह** |
| `hel` → **help** चुनें → `.` | `help.` (extra space नहीं) |
| Suggestion चुनें → Space | दूसरा space नहीं जुड़ता; दोबारा Space दबाएँ तो user का extra space रहता है |

## Notes

- Suggestions 100% offline curated data से हैं; कोई trained Gboard model या user learning नहीं।
- APK debug-signing key से signed है (preview distribution)। Same-package update के लिए इसी repository का अगला version use करें।
- वास्तविक फोन/OEM apps में E2E अभी verify बाकी है; build में 96 Java unit + browser/native-mock automated checks पास हैं (share-link guard: direct latest-download URL exactness check)।
