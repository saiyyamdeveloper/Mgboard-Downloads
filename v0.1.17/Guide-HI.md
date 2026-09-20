# Mgboard 0.1.17-share-download — Install और Share Guide

## नया क्या है

1. **Share बटन में सीधा download link + source link**: कीबोर्ड menu → Share पर अब यह text जाता है:

   ```
   Mgboard Android — मासरम गोंडी कीबोर्ड (0.1.17)
   नया version यहाँ से download करके install करें:
   https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest
   GitHub (source): https://github.com/saiyyamdeveloper/Mgboard
   ```

   जो download link प्राप्तकर्ता को मिलता है वह हमेशा इसी repository का **Latest release** page है — अगला version publish होते ही वही link नया version देगा।

   Note: source repository (`Mgboard`) अभी **private** है, इसलिए source link केवल reference के लिए है; download link हर हाल में public और काम करने वाला रहेगा।

2. **Scored suggestions (top 3)**: current prefix + पिछले committed शब्द के bigram context से तीन candidates; weights बाहरी config से (`w_lm=2.0, w_edit=1.5, w_freq=0.35`)।
3. **Guarded auto-space**: suggestion accept → एक space; अगली punctuation (`. , ? ! ; : । ॥` आदि) उसी space को अपने-आप हटाकर punctuation लिखती है; पहले से मौजूदा space duplicate नहीं होती; Enter trailing auto-space हटाकर newline/Send रखता है।

## Install

1. [Download](https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/download/v0.1.17/Mgboard-Android-0.1.17-share-download.apk) (या release page से) APK लाएँ।
2. Installer का पॉपअप में **Unknown sources** allow करें।
3. Install/Update करें — पहले से Mgboard हो तो Update, uninstall नहीं।
4. Settings → Keyboard → Mgboard select करें।

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
- वास्तविक फोन/OEM apps में E2E अभी verify बाकी है; build में 96 Java unit + browser/native-mock automated checks पास हैं (share-link guard: दोनों links की exactness check)।
