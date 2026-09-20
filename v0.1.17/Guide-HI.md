# Mgboard 0.1.17-space-scrub — Install और Share Guide

## नया क्या है

1. **Gboard-style spacebar cursor scrubbing**: spacebar अब **dual-mode** है —
   - **Tap** = space (पहले जैसा ही)।
   - **Horizontal drag** = text cursor scrub — अंगूठा spacebar पर रखकर बाएँ/दाएँ खींचो, cursor text में shift होता जाता है। धीमे खींचने पर ~12px per character step; **तेज़ flick करने पर cursor तेज़ी से दौड़ता है** (velocity-scaled, तक 2.2×)।
   - Scrub शुरू होने पर spacebar पर **`‹ ›` chevron + हल्की darkening** दिखती है — समझ आता है कि scrub mode चालू है।
   - हर character-step पर **haptic tick** (वibration settings off हों तो नहीं)।
   - Cursor **grapheme clusters** में move करता है — "किताब" में "कि" / "ता" / "ब" अखंड रहते हैं (consonant और उसके matra के बीच cursor नहीं फँसता); emoji families (👨‍👩‍👧), Gondi matras व flags भी whole-cluster।
   - Text की boundary (start/end) पर cursor clamp — आगे नहीं जाता।
   - Scrub के बाद अंगूठा छोड़ने पर **कोई space नहीं लगता**।
   - Scrub चालू होने के दौरान **दूसरी उंगली से दूसरी key dabane par commit नहीं होता** (ghost-tap lockout)।
   - Vertical slip (नीचे-ऊपर हिलाना) scrub नहीं बलता — release पर normal tap = space।
2. **Customize panel single-column**: pencil/pan icon (customise mode) दबाने पर अब **saare options ek hi panel mein, ek column mein, upar se neeche** dikhte hain — pehle jaisi left-right page-slide aur dots nahi; list **vertical scroll** hoti hai। Item ko toolbar row par drag karo = pin; wapas = unpin।
3. **Pin/unpin silent**: drag-drop se pin/unpin hota hai **chupke se** (item visibly apni jagah move karta hai) — "pin ho gaya/unpin ho gaya" wala popup nahi dikhta। Jab 6-pin ki limit cross ho toh **⚠️ warning still dikhti hai**।
4. **Gboard-style toolbar close button**: tools popup (4-dot grid दबाने से खुलने वाला) open होने पर top-left का **4-dot grid circular grey button + light ✕** बन जाता है — tap करने पर popup बंद। Customize mode (नीचे-दाएँ pencil/pan icon) दबाने पर वही जगह **✕ की जगह ✓** दिखता है — tap पर customize confirm। Popup बंद होने पर 4-dot grid वैसे का वैसे रहता है (वही popup खोलता है)।

   > Before/after (live browser preview): popup खुला = grey ✕; pencil दबाया = ✓ + single-column list; pencil फिर दबाया (customise off) = ✕ वापस + 2-column grid; row सदा visible — ताकि close ✕ कभी मत न हो।

5. **Share बटन में direct download link**: कीबोर्ड menu → Share पर अब सिर्फ यह text जाता है:

   ```
   Mgboard Android — मासरम गोंडी कीबोर्ड (0.1.17)
   नया version यहाँ से download करके install करें (direct download):
   https://github.com/saiyyamdeveloper/Mgboard-Downloads/releases/latest/download/Mgboard-Android-latest.apk
   ```

   Receiver यह link click करते ही **APK download seedha start** हो जाता है — बीच में कोई page नहीं। `latest` + stable asset name (`Mgboard-Android-latest.apk`) की वजह से अगला version publish होते ही वही link नया APK देगा।

   Install: download complete होने पर file पर tap करें → "Unknown sources" allow करें → install करें। (Android में install का tap सिस्टम security rule है — कोई app भी chupke se auto-install नहीं कर सकती।)

6. **Scored suggestions (top 3)**: current prefix + पिछले committed शब्द के bigram context से तीन candidates; weights बाहरी config से (`w_lm=2.0, w_edit=1.5, w_freq=0.35`)।
7. **Guarded auto-space**: suggestion accept → एक space; अगली punctuation (`. , ? ! ; : । ॥` आदि) उसी space को अपने-आप हटाकर punctuation लिखती है; पहले से मौजूदा space duplicate नहीं होती; Enter trailing auto-space हटाकर newline/Send रखता है।

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
- वास्तविक फोन/OEM apps में E2E अभी verify बाकी है; build में 96 Java unit + 929 browser/native-mock automated checks (1025 total) पास हैं (share-link guard: direct latest-download URL exactness; toolbar-x guard: grid → ✕ → ✓ → grid states; customize-panel guard: single-column list + silent pin/unpin + warning kept; space-scrub guard: tap=space, slow drag=exact steps, flick=accelerated, Devanagari+ZWJ grapheme edges, bounds, visual cue, two-finger ghost-tap lockout)।
