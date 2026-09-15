# Avalon

### Un PC Windows 10/11 x64. Più desktop indipendenti.

Avalon trasforma un host Windows 10/11 x64 in più istanze desktop accessibili in modo indipendente. Ogni istanza può avere la propria sessione Windows, display virtuale, input, audio, applicazioni, giochi e connessione Moonlight.

**Un host. Più istanze.**

[English](README.md)

[Registro di sviluppo e feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / bug e richieste](https://github.com/AvalonStream/AvalonStream/issues)

---

## Che cos’è Avalon?

Avalon è una piattaforma di streaming desktop multi-sessione per Windows 10/11 x64. Invece di dedicare l’intero PC a un solo desktop interattivo, consente a più istanze Windows indipendenti di funzionare sullo stesso host senza richiedere una macchina virtuale completa per ogni utente.

---

## Funzionalità principali

- Più istanze Windows indipendenti su un solo host
- Contesto di streaming dedicato per ogni istanza
- Display virtuale, risoluzione e frequenza di aggiornamento per istanza
- Percorsi indipendenti per tastiera, mouse e audio della sessione
- Avalon mantiene il ciclo di vita della sessione senza lasciare collegato un client RDP esterno
- Creazione, pairing, stato e diagnostica via Web
- Moonlight resta il client su telefoni, tablet, TV e PC

---

## Come funziona

Crea un’istanza, scegli le impostazioni del display e abbina il client. Avalon prepara la sessione Windows, il display virtuale, il contesto di streaming e il ciclo di vita; quindi ti connetti con Moonlight.

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

## Progettato per Moonlight

Avalon modifica il lato host senza sostituire il client che già conosci. Moonlight continua a funzionare su Windows, Linux, macOS, Android, iOS/iPadOS, Android TV e altri dispositivi supportati.

---

## Casi d’uso tipici

- Gaming domestico: persone diverse usano istanze diverse contemporaneamente
- Account multipli e carichi multi-istanza
- Più workstation remote su un unico PC potente
- Test, automazione e ambienti di compatibilità
- Homelab e calcolo remoto self-hosted

---

## Modello di isolamento

Avalon offre isolamento a livello di sessione Windows, non isolamento completo da macchina virtuale. Desktop, applicazioni, display, input e audio sono separati per istanza, ma Windows host, kernel, CPU, GPU e hardware fisico sono condivisi. Non va considerato un confine di sicurezza equivalente a una VM.

---

## Piattaforma e prestazioni

Avalon è destinato a Windows 10 e Windows 11 a 64 bit. Risoluzione, frequenza, codec, HDR e numero di istanze simultanee dipendono da GPU, driver, encoder, rete e hardware del client.

---

## Stato del progetto

Avalon è attualmente in fase Alpha. Interfaccia, compatibilità e componenti di basso livello sono ancora in evoluzione; sono quindi possibili modifiche incompatibili e casi limite legati all’hardware.

---

## Sviluppo e feedback

Questo README è la presentazione stabile del prodotto. Gli aggiornamenti di sviluppo in tempo reale e le indicazioni per i messaggi sono mantenuti separatamente nel registro di sviluppo.

- [Registro di sviluppo e feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / bug e richieste](https://github.com/AvalonStream/AvalonStream/issues)

**Un host. Più istanze.**
