# Avalon

### एक Windows 10/11 x64 PC. कई स्वतंत्र डेस्कटॉप।

Avalon एक Windows 10/11 x64 होस्ट को कई स्वतंत्र रूप से एक्सेस किए जा सकने वाले डेस्कटॉप इंस्टेंस में बदलता है। हर इंस्टेंस की अपनी Windows session, virtual display, input, audio, applications, games और Moonlight connection हो सकती है।

**एक host. कई instances.**

[English](README.md)

[Development log और feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / bugs और feature requests](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon क्या है?

Avalon Windows 10/11 x64 के लिए multi-session desktop streaming platform है। पूरे PC को केवल एक interactive desktop तक सीमित रखने के बजाय, यह हर user के लिए पूरी virtual machine चलाए बिना एक ही host पर कई independent Windows instances चलाने देता है।

---

## मुख्य क्षमताएँ

- एक host पर कई स्वतंत्र Windows instances
- हर instance के लिए अलग streaming context
- हर instance का virtual display, resolution और refresh rate
- अलग keyboard, mouse और session audio paths
- Avalon external RDP client को लगातार connected रखे बिना session lifecycle संभालता है
- Web से creation, pairing, status और diagnostics
- फोन, tablet, TV और PC पर परिचित Moonlight client ही इस्तेमाल होता है

---

## यह कैसे काम करता है?

एक instance बनाइए, display settings चुनिए और client pair कीजिए। Avalon Windows session, virtual display, streaming context और lifecycle तैयार करता है; इसके बाद Moonlight से connect करें।

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## Moonlight के लिए बनाया गया

Avalon उस client को बदलने के बजाय host side को व्यवस्थित करता है जिसे आप पहले से जानते हैं। Moonlight Windows, Linux, macOS, Android, iOS/iPadOS, Android TV और अन्य supported devices पर चलता रहता है।

---

## सामान्य उपयोग

- घर में gaming: अलग-अलग लोग एक साथ अलग instances इस्तेमाल करें
- कई accounts और multi-instance workloads
- एक शक्तिशाली PC पर कई remote workstations
- testing, automation और compatibility environments
- Homelab और self-hosted remote computing

---

## Isolation model

Avalon full virtual-machine isolation नहीं, बल्कि Windows session-level isolation देता है। Desktop, apps, displays, input और audio अलग रहते हैं, लेकिन host Windows, kernel, CPU, GPU और physical hardware साझा होते हैं। इसे VM-grade security boundary नहीं मानना चाहिए।

---

## Platform और performance

Avalon 64-bit Windows 10 और Windows 11 को target करता है। Resolution, refresh rate, codecs, HDR और simultaneous instances की संख्या GPU, drivers, encoder, network और client hardware पर निर्भर करती है।

---

## Project status

Avalon अभी Alpha stage में है। UI, compatibility और low-level components लगातार बदल रहे हैं, इसलिए breaking changes और hardware-specific edge cases संभव हैं।

---

## Development और feedback

यह README स्थिर product introduction है। Real-time development updates और message guidance अलग development log में रखे जाते हैं।

- [Development log और feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / bugs और feature requests](https://github.com/AvalonStream/AvalonStream/issues)

**एक host. कई instances.**
