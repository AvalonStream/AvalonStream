# Avalon

### Ein Windows-10/11-x64-PC. Mehrere unabhängige Desktops.

Avalon macht aus einem Windows-10/11-x64-Host mehrere unabhängig erreichbare Desktop-Instanzen. Jede Instanz kann eine eigene Windows-Sitzung, virtuelle Anzeige, Eingabe, Audioausgabe, Anwendungen, Spiele und Moonlight-Verbindung besitzen.

**Ein Host. Mehrere Instanzen.**

[English](README.md)

[Entwicklungsprotokoll & Feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / Fehler & Funktionswünsche](https://github.com/AvalonStream/AvalonStream/issues)

---

## Was ist Avalon?

Avalon ist eine Multi-Session-Desktop-Streaming-Plattform für Windows 10/11 x64. Statt den gesamten PC an einen einzigen interaktiven Desktop zu binden, können mehrere unabhängige Windows-Instanzen parallel auf demselben Host laufen – ohne für jeden Nutzer eine vollständige virtuelle Maschine bereitzustellen.

---

## Kernfunktionen

- Mehrere unabhängige Windows-Instanzen auf einem Host
- Eigener Streaming-Kontext pro Instanz
- Virtuelle Anzeige, Auflösung und Bildwiederholrate pro Instanz
- Getrennte Tastatur-, Maus- und Sitzungs-Audiopfade
- Avalon hält den Sitzungslebenszyklus aufrecht, ohne einen externen RDP-Client dauerhaft verbunden zu lassen
- Erstellung, Pairing, Status und Diagnose über die Weboberfläche
- Moonlight bleibt der Client auf Smartphones, Tablets, TVs und PCs

---

## So funktioniert es

Instanz erstellen, Anzeige konfigurieren und Client koppeln. Avalon richtet Windows-Sitzung, virtuelle Anzeige, Streaming-Kontext und Lebenszyklus ein; anschließend erfolgt die Verbindung über Moonlight.

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

## Für Moonlight entwickelt

Avalon verändert die Host-Seite und ersetzt nicht den vertrauten Client. Moonlight kann weiterhin unter Windows, Linux, macOS, Android, iOS/iPadOS, Android TV und weiteren unterstützten Geräten verwendet werden.

---

## Typische Einsatzbereiche

- Gaming zu Hause: mehrere Personen nutzen gleichzeitig unterschiedliche Instanzen
- Mehrere Konten und Multi-Instance-Workloads
- Mehrere Remote-Arbeitsplätze auf einem leistungsfähigen PC
- Tests, Automatisierung und Kompatibilitätsumgebungen
- Homelab und selbst gehostetes Remote Computing

---

## Isolationsmodell

Avalon bietet Isolation auf Windows-Sitzungsebene, keine vollständige VM-Isolation. Desktops, Anwendungen, Anzeigen, Eingabe und Audio sind pro Instanz getrennt, während Host-Windows, Kernel, CPU, GPU und physische Hardware gemeinsam genutzt werden. Avalon ist daher keine VM-äquivalente Sicherheitsgrenze.

---

## Plattform und Leistung

Avalon richtet sich an 64-Bit Windows 10 und Windows 11. Auflösung, Bildwiederholrate, Codecs, HDR und Anzahl gleichzeitiger Instanzen hängen von GPU, Treibern, Encoder, Netzwerk und Client-Hardware ab.

---

## Projektstatus

Avalon befindet sich derzeit in der Alpha-Phase. Oberfläche, Kompatibilität und Low-Level-Komponenten entwickeln sich weiter; inkompatible Änderungen und hardwarespezifische Randfälle sind daher möglich.

---

## Entwicklung und Feedback

Diese README ist die stabile Produktvorstellung. Laufende Entwicklungsupdates und Hinweise für Rückmeldungen werden separat im Entwicklungsprotokoll gepflegt.

- [Entwicklungsprotokoll & Feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / Fehler & Funktionswünsche](https://github.com/AvalonStream/AvalonStream/issues)

**Ein Host. Mehrere Instanzen.**
