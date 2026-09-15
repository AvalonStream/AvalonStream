<div align="center">

# Avalon

### Jeden komputer Windows 10/11 x64. Wiele niezależnych pulpitów.

Zamień pojedynczy komputer z Windows 10/11 x64 w wiele niezależnie dostępnych instancji pulpitu, z których każda ma własny ekran, wejście, dźwięk, aplikacje i połączenie zdalnego streamingu.

**Jeden host. Wiele instancji.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## Czym jest Avalon?

Avalon to platforma wielosesyjnego streamingu pulpitu dla Windows 10/11 x64.

Zamiast ograniczać komputer do jednego interaktywnego pulpitu, Avalon pozwala tej samej maszynie jednocześnie uruchamiać wiele niezależnych instancji Windows.

Każda instancja może mieć własne:

- sesję pulpitu Windows
- wirtualny ekran
- rozdzielczość i częstotliwość odświeżania
- strumień wejścia
- strumień audio
- aplikacje i gry
- zdalne połączenie przez Moonlight

Dzięki temu jeden wydajny komputer może działać bardziej jak kilka zdalnie dostępnych komputerów, bez konieczności uruchamiania pełnej maszyny wirtualnej dla każdego użytkownika.

---

## Jak wygląda to w praktyce?

Wyobraź sobie komputer Windows 10/11 x64 z trzema instancjami Avalon:

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

Każdy klient łączy się z własnym pulpitem Windows.

Instancje działają równolegle bez współdzielenia tego samego pulpitu, kursora myszy, wyjścia audio ani sesji aplikacji.

---

## Dlaczego Avalon?

Tradycyjne narzędzia pulpitu zdalnego są zwykle projektowane wokół modelu, w którym jeden użytkownik steruje jednym pulpitem.

Maszyny wirtualne zapewniają silną izolację, ale wymagają również dodatkowych systemów operacyjnych, większej ilości pamięci, przestrzeni dyskowej, bardziej złożonej obsługi GPU i większych kosztów administracyjnych.

Avalon wybiera inne podejście.

Łączy sesje Windows, wirtualne ekrany, niezależne procesy streamingu i scentralizowane zarządzanie cyklem życia, dzięki czemu wiele interaktywnych pulpitów może współistnieć na jednym hoście Windows 10/11 x64.

Złożoność pozostaje wewnątrz Avalon. Dla użytkownika przepływ jest prosty:

```text
Utwórz instancję
        ↓
Skonfiguruj ekran i parowanie
        ↓
Uruchom Moonlight
        ↓
Połącz się
```

---

## Najważniejsze możliwości

### Wiele niezależnych instancji

Uruchamiaj jednocześnie wiele sesji pulpitu Windows na jednym hoście.

Każda instancja zachowuje się jak oddzielne interaktywne środowisko pulpitu.

### Niezależny streaming

Każda instancja ma własny kontekst streamingu i może być niezależnie obsługiwana przez klienta Moonlight.

Telewizor może być połączony z jedną instancją, podczas gdy tablet lub inny komputer jednocześnie łączy się z inną.

### Niezależny ekran

Każda instancja może używać własnej konfiguracji wirtualnego ekranu, w tym rozdzielczości i częstotliwości odświeżania.

Avalon zarządza środowiskiem wyświetlania bez konieczności posiadania fizycznego monitora dla każdej instancji.

### Niezależne wejście

Klawiatura i mysz są kierowane do właściwej sesji Windows zamiast być współdzielone między wszystkimi instancjami.

Wraz z rozwojem warstwy wejścia Avalon jest projektowany z myślą o coraz pełniejszej izolacji urządzeń na poziomie pojedynczej instancji.

### Niezależne audio

Każda instancja korzysta z własnej ścieżki audio sesji Windows, dzięki czemu różni użytkownicy mogą słuchać różnych aplikacji i gier bez prostego mieszania dźwięku między instancjami.

### Zarządzanie cyklem życia sesji

Avalon sam tworzy i utrzymuje sesje.

Nie trzeba pozostawiać stale podłączonego zewnętrznego klienta RDP tylko po to, aby instancja pozostała aktywna.

### Zarządzanie przez Web

Wszystkie instancje są zarządzane z jednego interfejsu Web.

Typowe operacje obejmują:

- tworzenie i usuwanie instancji
- uruchamianie i zatrzymywanie instancji
- konfigurację rozdzielczości i częstotliwości odświeżania
- parowanie klientów Moonlight
- sprawdzanie stanu połączenia
- przeglądanie diagnostyki
- zarządzanie ustawieniami hosta

Codzienne użycie nie wymaga wiersza poleceń.

---

## Zaprojektowany dla Moonlight

Avalon zachowuje znane doświadczenie streamingu Moonlight.

Moonlight może być nadal używany na urządzeniach takich jak:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Smart TV i urządzenia streamingowe obsługiwane przez Moonlight

Avalon zmienia organizację po stronie hosta, a nie wymusza nauki zupełnie nowego klienta streamingu.

---

## Przykładowe zastosowania

### Granie w domu

Zamień jeden komputer gamingowy w wiele niezależnych środowisk do grania dla różnych osób w tym samym domu.

Jedna osoba może grać na telewizorze w salonie, podczas gdy druga łączy się z inną instancją z urządzenia przenośnego lub laptopa.

### Wiele kont i wiele instancji

Uruchamiaj różne aplikacje, konta lub sesje gier w oddzielnych środowiskach Windows na tej samej maszynie.

### Zdalna stacja robocza

Wykorzystaj wydajny komputer stacjonarny jako kilka niezależnie dostępnych zdalnych środowisk pracy.

### Testowanie i rozwój

Utrzymuj wiele sesji Windows do testowania oprogramowania, automatyzacji, sprawdzania kompatybilności lub izolowanych środowisk użytkownika.

### Homelab i self-hosting

Wykorzystaj wydajny komputer Windows jako centralnie zarządzany, wieloużytkownikowy host zdalnego przetwarzania.

---

## Jak działa Avalon

Avalon wewnętrznie koordynuje kilka warstw systemu:

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

Zwykły użytkownik nie musi rozumieć tych szczegółów implementacyjnych.

Tworzysz instancję; Avalon przygotowuje sesję, ekran, środowisko streamingu i cykl życia; następnie się łączysz.

---

## Model izolacji

Avalon zapewnia **izolację na poziomie sesji Windows**.

Każda instancja ma własną sesję Windows, pulpit, aplikacje, ekran, ścieżkę wejścia i ścieżkę audio.

Instancje Avalon **nie są jednak pełnymi maszynami wirtualnymi**.

Nadal współdzielą:

- tę samą instalację Windows hosta
- ten sam kernel
- ten sam fizyczny CPU
- ten sam fizyczny GPU
- te same zasoby sprzętowe hosta

Avalon nie powinien więc być traktowany jako granica bezpieczeństwa na poziomie VM.

Celem jest wydajny streaming wieloużytkownikowy i wielopulpitowy, a nie pełna wirtualizacja sprzętu.

---

## Aktualny stan

Avalon znajduje się obecnie w fazie **Alpha**.

Architektura, interfejs zarządzania, warstwa kompatybilności i stos urządzeń są nadal rozwijane.

Na tym etapie mogą występować:

- zmiany niekompatybilne
- niepełna kompatybilność sprzętowa
- zmiany interfejsu użytkownika
- przypadki brzegowe związane ze sterownikami i sesjami
- funkcje, których zachowanie może się zmienić przed wydaniem stabilnym

Avalon nie jest jeszcze przeznaczony do użycia jako krytyczna infrastruktura produkcyjna.

Testy, logi, odtwarzalne raporty błędów i informacje z rzeczywistego użytkowania są na tym etapie szczególnie cenne.

---

## Platforma

Aktualny cel:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon jest projektowany konkretnie wokół modelu pulpitu, sesji i grafiki Windows.

Obsługa innych systemów operacyjnych hosta nie jest obecnie głównym celem projektu.

---

## Wydajność

Rzeczywista wydajność streamingu zależy od wielu czynników, w tym:

- GPU
- obsługi enkodera
- sterownika graficznego
- rozdzielczości
- częstotliwości odświeżania
- kodeka
- jakości sieci
- możliwości dekodowania klienta
- liczby jednocześnie działających instancji

Avalon nie gwarantuje określonej rozdzielczości, częstotliwości odświeżania, trybu HDR ani liczby równoczesnych instancji na każdym systemie.

Dokumentacja kompatybilności będzie rozwijana wraz z rozszerzaniem testów.

---

## Filozofia projektu

Avalon opiera się na prostej idei:

> Wydajny komputer nie powinien być na stałe ograniczony do jednego ekranu, jednego pulpitu i jednego użytkownika.

Host może być jedną maszyną. Doświadczenia działające na nim nie muszą być tylko jedne.

---

## Rozwój

Ten README jest utrzymywany jako stabilne wprowadzenie do produktu Avalon.

Bieżące informacje o rozwoju i komunikaty projektu znajdziesz w [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Błędy, pytania i propozycje funkcji zgłaszaj przez [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Jeden host. Wiele instancji.**

</div>
