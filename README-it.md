<div align="center">

# Avalon

### Un PC Windows 10/11 x64. Più desktop indipendenti.

Trasforma un singolo computer Windows 10/11 x64 in più istanze desktop accessibili in modo indipendente, ciascuna con il proprio display, input, audio, applicazioni e connessione di streaming remoto.

**Un host. Più istanze.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## Che cos’è Avalon?

Avalon è una piattaforma di streaming desktop multi-sessione per Windows 10/11 x64.

Invece di limitare un PC a un solo desktop interattivo, Avalon consente alla stessa macchina di ospitare contemporaneamente più istanze Windows indipendenti.

Ogni istanza può avere i propri:

- sessione desktop Windows
- display virtuale
- risoluzione e frequenza di aggiornamento
- flusso di input
- flusso audio
- applicazioni e giochi
- connessione remota tramite Moonlight

In questo modo un singolo PC potente può comportarsi più come diversi computer accessibili da remoto, senza richiedere una macchina virtuale completa per ogni utente.

---

## Come appare nella pratica?

Immagina un PC Windows 10/11 x64 che esegue tre istanze Avalon:

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

Ogni client si collega al proprio desktop Windows.

Le istanze funzionano in parallelo senza condividere lo stesso desktop, il cursore del mouse, l’uscita audio o la stessa sessione applicativa.

---

## Perché Avalon?

Gli strumenti tradizionali di desktop remoto sono generalmente progettati attorno a un utente che controlla un singolo desktop.

Le macchine virtuali offrono un forte isolamento, ma aggiungono anche sistemi operativi completi, maggiore uso di memoria e storage, più complessità nella gestione della GPU e costi amministrativi superiori.

Avalon segue un approccio diverso.

Combina sessioni Windows, display virtuali, processi di streaming indipendenti e gestione centralizzata del ciclo di vita, permettendo a più desktop interattivi di convivere sullo stesso host Windows 10/11 x64.

La complessità rimane all’interno di Avalon. Per l’utente, il flusso è semplice:

```text
Crea un'istanza
        ↓
Configura display e associazione
        ↓
Apri Moonlight
        ↓
Connettiti
```

---

## Funzionalità principali

### Più istanze indipendenti

Esegui contemporaneamente più sessioni desktop Windows sullo stesso host.

Ogni istanza si comporta come un ambiente desktop interattivo separato.

### Streaming indipendente

Ogni istanza ha il proprio contesto di streaming e può essere raggiunta separatamente tramite un client Moonlight.

Un televisore può collegarsi a un’istanza mentre un tablet o un altro computer si collega contemporaneamente a un’altra.

### Display indipendente

Ogni istanza può utilizzare la propria configurazione di display virtuale, inclusi risoluzione e frequenza di aggiornamento.

Avalon gestisce l’ambiente video senza richiedere un monitor fisico per ogni istanza.

### Input indipendente

Tastiera e mouse vengono instradati verso la sessione Windows corretta invece di essere condivisi tra tutte le istanze.

Con l’evoluzione dello stack di input, Avalon è progettato per avvicinarsi a un isolamento dei dispositivi sempre più completo per singola istanza.

### Audio indipendente

Ogni istanza usa il proprio percorso audio della sessione Windows, così utenti diversi possono ascoltare applicazioni o giochi diversi senza mescolare semplicemente l’audio tra le istanze.

### Gestione del ciclo di vita delle sessioni

Avalon crea e mantiene direttamente le sessioni.

Non è necessario lasciare collegato un client RDP esterno solo per mantenere viva un’istanza.

### Gestione Web

Tutte le istanze vengono amministrate da un’unica interfaccia Web.

Le operazioni tipiche comprendono:

- creare e rimuovere istanze
- avviare e arrestare istanze
- configurare risoluzione e frequenza di aggiornamento
- associare client Moonlight
- controllare lo stato delle connessioni
- visualizzare informazioni diagnostiche
- gestire impostazioni a livello host

Per l’uso quotidiano non è necessaria la riga di comando.

---

## Progettato per Moonlight

Avalon mantiene l’esperienza di streaming Moonlight già familiare.

Puoi continuare a usare Moonlight su dispositivi come:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Smart TV e dispositivi di streaming supportati da Moonlight

Avalon cambia l’organizzazione lato host; non obbliga a imparare un client di streaming completamente nuovo.

---

## Casi d’uso

### Gaming domestico

Trasforma un singolo PC da gioco in più ambienti gaming indipendenti per persone diverse nella stessa casa.

Una persona può giocare dal televisore del soggiorno mentre un’altra si collega a un’altra istanza da un handheld o da un portatile.

### Account multipli e istanze multiple

Esegui applicazioni, account o sessioni di gioco differenti in ambienti Windows separati sulla stessa macchina.

### Workstation remota

Usa un desktop potente come più spazi di lavoro remoti accessibili indipendentemente.

### Test e sviluppo

Mantieni più sessioni Windows per test software, automazione, verifica di compatibilità o ambienti utente isolati.

### Homelab e self-hosting

Usa una macchina Windows ad alte prestazioni come host di calcolo remoto multiutente gestito centralmente.

---

## Come funziona Avalon

Avalon coordina internamente diversi livelli del sistema:

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

Gli utenti normali non devono conoscere questi dettagli implementativi.

Crei un’istanza; Avalon prepara sessione, display, ambiente di streaming e ciclo di vita; quindi ti connetti.

---

## Modello di isolamento

Avalon offre **isolamento a livello di sessione Windows**.

Ogni istanza dispone della propria sessione Windows, desktop, applicazioni, display, percorso di input e percorso audio.

Tuttavia, le istanze Avalon **non sono macchine virtuali complete**.

Continuano a condividere:

- la stessa installazione Windows dell’host
- lo stesso kernel
- la stessa CPU fisica
- la stessa GPU fisica
- le stesse risorse hardware dell’host

Avalon non deve quindi essere considerato un confine di sicurezza equivalente a quello di una VM.

L’obiettivo è offrire streaming multiutente e multi-desktop efficiente, non virtualizzazione hardware completa.

---

## Stato attuale

Avalon è attualmente in fase **Alpha**.

Architettura, interfaccia di gestione, livello di compatibilità e stack dei dispositivi continuano a evolversi.

In questa fase possono verificarsi:

- modifiche incompatibili
- compatibilità hardware incompleta
- modifiche all’interfaccia
- casi limite relativi a driver e sessioni
- funzionalità il cui comportamento può cambiare prima della versione stabile

Avalon non è ancora destinato a essere usato come infrastruttura critica di produzione.

Test, log, segnalazioni di bug riproducibili e feedback da utilizzo reale sono particolarmente preziosi in questa fase.

---

## Piattaforma

Obiettivo attuale:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon è progettato specificamente attorno al modello desktop, sessioni e grafica di Windows.

Il supporto per altri sistemi operativi host non è attualmente un obiettivo principale del progetto.

---

## Prestazioni

Le prestazioni reali dello streaming dipendono da molti fattori, tra cui:

- GPU
- supporto dell’encoder
- driver grafico
- risoluzione
- frequenza di aggiornamento
- codec
- qualità della rete
- capacità di decodifica del client
- numero di istanze simultanee

Avalon non garantisce una specifica risoluzione, frequenza di aggiornamento, modalità HDR o un numero fisso di istanze contemporanee su ogni sistema.

La documentazione sulla compatibilità verrà ampliata con l’aumentare dei test.

---

## Filosofia del progetto

Avalon nasce da un’idea semplice:

> Un PC potente non dovrebbe essere sempre limitato a uno schermo, un desktop e un solo utente.

L’host può essere una sola macchina. Le esperienze che vi vengono eseguite non devono necessariamente essere una sola.

---

## Sviluppo

Questo README viene mantenuto come introduzione stabile al prodotto Avalon.

Per aggiornamenti di sviluppo in tempo reale e messaggi del progetto, consulta [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Per segnalare bug, fare domande o proporre funzionalità, usa [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Un host. Più istanze.**

</div>
