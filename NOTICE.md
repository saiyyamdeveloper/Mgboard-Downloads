# NOTICE — Mgboard-Downloads

यह public repository केवल binary APK distribution के लिए है।

## स्रोत और मालिकाना हक

- Mgboard कीबोर्ड का स्रोत कोड `saiyyamdeveloper` के private GitHub repository में है।
- APK `web-source/index.html` (frozen, SHA-256 `01b888852ff59d2461cf54479e9e2c747a1b6ba4f543b6d2fc4058e187d98731`) + Android adapter + native Java shell से बना है।
- Repository owner ने इस web-based Android keyboard को adapt/publish करने की अनुमति दी है; upstream notices APK के `assets/licenses/` में bundled हैं।

## Bundled third-party components

- **Noto Sans Masaram Gondi** — SIL Open Font License 1.1 (APK में `assets/fonts/` + `assets/licenses/NotoSansMasaramGondi-OFL.txt`)।
- Android platform libraries (AOSP, Apache-2.0)।
- कोई Google/Gboard model, binary या data bundled **नहीं** है।

## Suggestions data

0.1.17 के scored-suggestions dictionaries (784 English / 844 Hindi / 624 Hinglish) और 168 bigram pairs स्वतंत्र रूप से हाथ से तैयार illustrative data हैं। `curated_priority` एक manually assigned pseudo-frequency है — observed corpus या user frequency नहीं। कोई trained/proprietary language model शामिल नहीं है।

## Signing

APK debug signing key से signed है; production release key नहीं।
