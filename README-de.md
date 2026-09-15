<div align="center">

# Avalon

### Ein Windows-10/11-x64-PC. Mehrere unabhängige Desktops.

Verwandle einen einzelnen Windows-10/11-x64-Rechner in mehrere unabhängig erreichbare Desktop-Instanzen – jeweils mit eigener Anzeige, Eingabe, Audioausgabe, Anwendungen und eigener Remote-Streaming-Verbindung.

**Ein Host. Mehrere Instanzen.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## Was ist Avalon?

Avalon ist eine Multi-Session-Desktop-Streaming-Plattform für Windows 10/11 x64.

Anstatt einen PC auf nur einen interaktiven Desktop zu beschränken, kann derselbe Rechner mehrere unabhängige Windows-Instanzen gleichzeitig bereitstellen.

Jede Instanz kann über eigene Komponenten verfügen:

- Windows-Desktop-Sitzung
- virtueller Bildschirm
- Auflösung und Bildwiederholrate
- Eingabestrom
- Audiostrom
- Anwendungen und Spiele
- Remote-Verbindung über Moonlight

So kann sich ein leistungsfähiger PC eher wie mehrere aus der Ferne erreichbare Rechner verhalten, ohne für jeden Benutzer eine vollständige virtuelle Maschine ausführen zu müssen.

---

## Wie sieht das praktisch aus?

Beispiel: Ein Windows-10/11-x64-PC führt drei Avalon-Instanzen aus.

```text
                Windows 10/11 x64 Host
                       │
                ┌──────┴──────┐
                │    Avalon    │
                └──────┬──────┘
                       │
         ┌─────────────┼─────────────┐
         │             │             │
         ▼             ▼             ▼
    Instance 01    Instance 02    Instance 03
         │             │             │
         ▼             ▼             ▼
     Moonlight      Moonlight      Moonlight
        TV            Tablet         Laptop
```

Jeder Client verbindet sich mit seinem eigenen Windows-Desktop.

Die Instanzen laufen parallel, ohne denselben Desktop, Mauszeiger, Audioausgang oder dieselbe Anwendungssitzung zu teilen.

---

## Warum Avalon?

Klassische Remote-Desktop-Werkzeuge sind meist für einen Benutzer ausgelegt, der einen einzelnen Desktop steuert.

Virtuelle Maschinen bieten starke Isolation, bringen aber zusätzliche Betriebssysteme, höheren Speicherbedarf, mehr Storage-Verbrauch, komplexere GPU-Konfigurationen und zusätzlichen Verwaltungsaufwand mit sich.

Avalon verfolgt einen anderen Ansatz.

Windows-Sitzungen, virtuelle Displays, unabhängige Streaming-Prozesse und eine zentrale Lebenszyklusverwaltung werden kombiniert, sodass mehrere interaktive Desktops auf einem einzigen Windows-10/11-x64-Host gleichzeitig existieren können.

Die Komplexität bleibt in Avalon. Für den Benutzer ist der Ablauf einfach:

```text
Instanz erstellen
        ↓
Anzeige und Pairing konfigurieren
        ↓
Moonlight öffnen
        ↓
Verbinden
```

---

## Kernfunktionen

### Mehrere unabhängige Instanzen

Mehrere Windows-Desktop-Sitzungen können gleichzeitig auf demselben Host ausgeführt werden.

Jede Instanz verhält sich wie eine eigene interaktive Desktop-Umgebung.

### Unabhängiges Streaming

Jede Instanz besitzt ihren eigenen Streaming-Kontext und kann separat über einen Moonlight-Client erreicht werden.

Ein Fernseher kann mit einer Instanz verbunden sein, während ein Tablet oder ein anderer PC gleichzeitig eine andere Instanz nutzt.

### Unabhängige Anzeige

Jede Instanz kann ihre eigene virtuelle Anzeige mit eigener Auflösung und Bildwiederholrate verwenden.

Avalon verwaltet die Anzeigeumgebung, sodass nicht für jede Instanz ein physischer Monitor erforderlich ist.

### Unabhängige Eingabe

Tastatur- und Mauseingaben werden an die vorgesehene Windows-Sitzung weitergeleitet, anstatt zwischen allen Instanzen geteilt zu werden.

Mit der Weiterentwicklung des Input-Stacks ist Avalon darauf ausgelegt, die Geräteisolation pro Instanz weiter zu vervollständigen.

### Unabhängiges Audio

Jede Instanz nutzt ihren eigenen Windows-Sitzungs-Audiopfad. Dadurch können unterschiedliche Benutzer verschiedene Anwendungen oder Spiele hören, ohne dass die Audiosignale einfach zwischen den Instanzen vermischt werden.

### Lebenszyklusverwaltung der Sitzungen

Avalon erstellt und hält die Sitzungen selbstständig aufrecht.

Ein externer RDP-Client muss nicht dauerhaft verbunden bleiben, nur damit eine Instanz weiterläuft.

### Web-Verwaltung

Alle Instanzen werden über eine zentrale Web-Oberfläche verwaltet.

Typische Vorgänge sind:

- Instanzen erstellen und entfernen
- Instanzen starten und stoppen
- Auflösung und Bildwiederholrate konfigurieren
- Moonlight-Clients koppeln
- Verbindungsstatus prüfen
- Diagnoseinformationen anzeigen
- Host-weite Einstellungen verwalten

Für den normalen Alltag ist keine Kommandozeile erforderlich.

---

## Für Moonlight entwickelt

Avalon behält die vertraute Moonlight-Streaming-Erfahrung bei.

Moonlight kann weiterhin auf folgenden Geräten verwendet werden:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Smart-TVs und Streaming-Geräte mit Moonlight-Unterstützung

Avalon verändert die Organisation auf der Host-Seite. Benutzer müssen keinen völlig neuen Streaming-Client lernen.

---

## Einsatzmöglichkeiten

### Gaming zu Hause

Ein einzelner Gaming-PC kann mehrere unabhängige Spielumgebungen für verschiedene Personen im selben Haushalt bereitstellen.

Eine Person kann am Fernseher im Wohnzimmer spielen, während eine andere gleichzeitig von einem Handheld oder Laptop auf eine andere Instanz zugreift.

### Mehrere Konten und Instanzen

Verschiedene Anwendungen, Konten oder Spielsitzungen können in getrennten Windows-Umgebungen auf demselben Rechner laufen.

### Remote-Workstation

Ein leistungsfähiger Desktop kann als mehrere unabhängig erreichbare Remote-Arbeitsplätze genutzt werden.

### Tests und Entwicklung

Mehrere Windows-Sitzungen können für Softwaretests, Automatisierung, Kompatibilitätsprüfungen oder getrennte Benutzerumgebungen bereitgehalten werden.

### Homelab und Self-Hosting

Ein leistungsfähiger Windows-Rechner kann als zentral verwalteter Multi-User-Remote-Compute-Host dienen.

---

## Wie Avalon funktioniert

Avalon koordiniert intern mehrere Systemebenen:

```text
Web Management
      │
      ▼
Avalon Control Service
      │
      ▼
Windows Sessions
Virtual Displays
Streaming Processes
Input / Audio Routing
      │
      ▼
Moonlight Clients
```

Normale Benutzer müssen diese internen Implementierungsdetails nicht verstehen.

Du erstellst eine Instanz; Avalon bereitet Sitzung, Anzeige, Streaming-Umgebung und Lebenszyklus vor; anschließend verbindest du dich.

---

## Isolationsmodell

Avalon bietet **Isolation auf Windows-Sitzungsebene**.

Jede Instanz besitzt eine eigene Windows-Sitzung, einen eigenen Desktop, eigene Anwendungen, Anzeige-, Eingabe- und Audiopfade.

Avalon-Instanzen sind jedoch **keine vollständigen virtuellen Maschinen**.

Sie teilen weiterhin:

- dieselbe Windows-Host-Installation
- denselben Kernel
- dieselbe physische CPU
- dieselbe physische GPU
- dieselben Hardware-Ressourcen des Hosts

Avalon sollte daher nicht als Sicherheitsgrenze auf VM-Niveau betrachtet werden.

Das Ziel ist effizientes Multi-User- und Multi-Desktop-Streaming, nicht vollständige Hardwarevirtualisierung.

---

## Aktueller Status

Avalon befindet sich derzeit in der **Alpha-Phase**.

Architektur, Verwaltungsoberfläche, Kompatibilitätsschicht und Geräte-Stack werden weiterhin entwickelt.

In dieser Phase sind unter anderem möglich:

- inkompatible Änderungen
- unvollständige Hardware-Kompatibilität
- UI-Änderungen
- Randfälle bei Treibern und Sitzungen
- Funktionen, deren Verhalten sich vor einer stabilen Version noch ändert

Avalon ist noch nicht als produktionskritische Infrastruktur gedacht.

Tests, Logs, reproduzierbare Fehlerberichte und Rückmeldungen aus realer Nutzung sind in dieser Phase besonders wertvoll.

---

## Plattform

Aktuelles Ziel:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon ist speziell auf das Desktop-, Sitzungs- und Grafikmodell von Windows ausgelegt.

Andere Host-Betriebssysteme gehören derzeit nicht zu den Hauptzielen des Projekts.

---

## Leistung

Die tatsächliche Streaming-Leistung hängt von vielen Faktoren ab, darunter:

- GPU
- Encoder-Unterstützung
- Grafiktreiber
- Auflösung
- Bildwiederholrate
- Codec
- Netzwerkqualität
- Decoder-Leistung des Clients
- Anzahl gleichzeitig laufender Instanzen

Avalon garantiert nicht auf jedem System eine bestimmte Auflösung, Bildwiederholrate, einen HDR-Modus oder eine feste Anzahl gleichzeitiger Instanzen.

Mit wachsender Testabdeckung wird auch die Kompatibilitätsdokumentation detaillierter.

---

## Projektphilosophie

Avalon basiert auf einer einfachen Idee:

> Ein leistungsfähiger PC sollte nicht dauerhaft auf einen Bildschirm, einen Desktop und einen Benutzer beschränkt sein.

Der Host kann eine einzige Maschine sein. Die darauf laufenden Nutzungserlebnisse müssen nicht auf eines beschränkt bleiben.

---

## Entwicklung

Dieses README dient als stabile Produkteinführung für Avalon.

Aktuelle Entwicklungsfortschritte und Projektmeldungen findest du in [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Fehlerberichte, Fragen und Funktionswünsche gehören in [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Ein Host. Mehrere Instanzen.**

</div>
