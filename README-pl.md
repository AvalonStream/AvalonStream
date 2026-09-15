# Avalon

### Jeden komputer Windows 10/11 x64. Wiele niezależnych pulpitów.

Avalon zmienia jeden host Windows 10/11 x64 w wiele niezależnie dostępnych instancji pulpitu. Każda instancja może mieć własną sesję Windows, wirtualny ekran, wejście, dźwięk, aplikacje, gry oraz połączenie Moonlight.

**Jeden host. Wiele instancji.**

[English](README.md)

[Dziennik rozwoju i opinie](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / błędy i propozycje](https://github.com/AvalonStream/AvalonStream/issues)

---

## Czym jest Avalon?

Avalon to wielosesyjna platforma strumieniowania pulpitu dla Windows 10/11 x64. Zamiast przeznaczać cały komputer na jeden interaktywny pulpit, pozwala uruchamiać kilka niezależnych instancji Windows na tym samym hoście bez pełnej maszyny wirtualnej dla każdego użytkownika.

---

## Najważniejsze możliwości

- Wiele niezależnych instancji Windows na jednym hoście
- Oddzielny kontekst strumieniowania dla każdej instancji
- Wirtualny ekran, rozdzielczość i częstotliwość odświeżania dla każdej instancji
- Niezależne ścieżki klawiatury, myszy i dźwięku sesji
- Avalon utrzymuje cykl życia sesji bez ciągłego połączenia zewnętrznego klienta RDP
- Tworzenie, parowanie, stan i diagnostyka przez Web
- Moonlight pozostaje klientem na telefonach, tabletach, TV i komputerach

---

## Jak to działa

Utwórz instancję, wybierz ustawienia ekranu i sparuj klienta. Avalon przygotuje sesję Windows, wirtualny ekran, kontekst strumieniowania i cykl życia; następnie łączysz się przez Moonlight.

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

## Zaprojektowany dla Moonlight

Avalon zmienia stronę hosta, a nie znanego już klienta. Moonlight nadal działa na Windows, Linux, macOS, Android, iOS/iPadOS, Android TV i innych obsługiwanych urządzeniach.

---

## Typowe zastosowania

- Granie w domu: różne osoby korzystają jednocześnie z różnych instancji
- Wiele kont i obciążenia wieloinstancyjne
- Kilka zdalnych stanowisk na jednym wydajnym PC
- Testy, automatyzacja i środowiska zgodności
- Homelab i samodzielnie hostowane zdalne obliczenia

---

## Model izolacji

Avalon zapewnia izolację na poziomie sesji Windows, a nie pełną izolację maszyny wirtualnej. Pulpity, aplikacje, ekrany, wejście i audio są rozdzielone, ale system hosta, kernel, CPU, GPU i sprzęt fizyczny są współdzielone. Nie należy traktować go jako granicy bezpieczeństwa klasy VM.

---

## Platforma i wydajność

Avalon jest przeznaczony dla 64-bitowych Windows 10 i Windows 11. Rozdzielczość, odświeżanie, kodeki, HDR i liczba jednoczesnych instancji zależą od GPU, sterowników, enkodera, sieci i sprzętu klienta.

---

## Stan projektu

Avalon znajduje się obecnie w fazie Alpha. Interfejs, zgodność i komponenty niskiego poziomu nadal się zmieniają, dlatego możliwe są zmiany niekompatybilne i problemy specyficzne dla sprzętu.

---

## Rozwój i opinie

Ten README jest stabilnym opisem produktu. Bieżące informacje o rozwoju i zasady przekazywania uwag znajdują się w osobnym dzienniku rozwoju.

- [Dziennik rozwoju i opinie](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / błędy i propozycje](https://github.com/AvalonStream/AvalonStream/issues)

**Jeden host. Wiele instancji.**
