# Agent AI – automatyzacja obsługi wiadomości e-mail

## Opis projektu

Agent AI automatyzujący analizę wiadomości e-mail od klientów oraz przygotowywanie propozycji odpowiedzi na podstawie firmowej bazy wiedzy.

System automatycznie odbiera nowe wiadomości, analizuje ich treść z wykorzystaniem modelu OpenAI i przygotowuje wersje robocze odpowiedzi w Gmailu. Pracownik może następnie sprawdzić, edytować i wysłać gotową propozycję.

Rozwiązanie ogranicza czas poświęcany na obsługę powtarzalnych zapytań i wspiera pracowników w codziennej komunikacji z klientami.

## Problem biznesowy

Obsługa poczty elektronicznej często wymaga od pracowników wykonywania powtarzalnych czynności:

- czytania i analizowania każdej wiadomości,
- wyszukiwania potrzebnych informacji w dokumentacji firmy,
- przygotowywania odpowiedzi na podobne pytania,
- ręcznego tworzenia wiadomości zwrotnych.

Przy dużej liczbie zapytań czynności te zajmują znaczną część czasu pracy i ograniczają możliwość skupienia się na bardziej wymagających zadaniach.

## Zastosowane rozwiązanie

Agent AI automatyzuje proces przygotowywania odpowiedzi na wiadomości klientów.

Po otrzymaniu nowej wiadomości system:

1. Automatycznie odbiera wiadomość za pośrednictwem mechanizmu Mailhook.
2. Pobiera informacje z firmowej bazy wiedzy przechowywanej w Google Docs.
3. Przekazuje treść wiadomości oraz bazę wiedzy do modelu OpenAI.
4. Analizuje zapytanie i generuje propozycję odpowiedzi.
5. Tworzy wersję roboczą wiadomości w Gmailu.

Pracownik otrzymuje gotowy draft, który może zweryfikować, zmodyfikować i wysłać do klienta.

System nie wysyła wiadomości automatycznie.

## Architektura systemu

**Przepływ danych:**

Gmail → Automatyczne przekazywanie wiadomości → Make Mailhook → Filtr wiadomości → Google Docs → OpenAI API → Gmail (wersja robocza odpowiedzi)

### Wykorzystane komponenty

| Komponent | Rola w systemie |
|---|---|
| Gmail | Odbieranie wiadomości klientów i przechowywanie przygotowanych odpowiedzi |
| Make Mailhook | Automatyczne uruchamianie scenariusza po otrzymaniu przekazanej wiadomości |
| Make | Integracja usług i koordynacja całego procesu |
| Google Docs | Przechowywanie firmowej bazy wiedzy |
| OpenAI API | Analiza wiadomości i generowanie propozycji odpowiedzi |

## Funkcjonalności

- **Automatyczne uruchamianie** – system reaguje na nowe wiadomości bez konieczności cyklicznego sprawdzania skrzynki.
- **Filtrowanie wiadomości** – możliwość pomijania wybranych wiadomości automatycznych i wiadomości wysłanych z własnego konta.
- **Analiza wiadomości** – model AI interpretuje treść zapytania klienta.
- **Firmowa baza wiedzy** – odpowiedzi są przygotowywane na podstawie informacji przechowywanych w Google Docs.
- **Generowanie odpowiedzi** – AI tworzy propozycję odpowiedzi dopasowaną do otrzymanego zapytania.
- **Tworzenie wersji roboczych** – gotowe propozycje są zapisywane w Gmailu.
- **Kontrola pracownika** – każda odpowiedź może zostać sprawdzona i edytowana przed wysłaniem.

## Przykładowe działanie systemu

### 1. Scenariusz automatyzacji w Make

<img width="856" height="268" alt="image" src="https://github.com/user-attachments/assets/6f1cfb24-8f02-4d68-b9e6-2cc828400a82" />


### 2. Baza wiedzy przykładowej firmy

<img width="800" height="831" alt="image" src="https://github.com/user-attachments/assets/2c97b4f2-6bc1-49f6-a5cd-6ac20d15d1a8" />


### 3. Instrukcje systemowe modelu AI

<img width="377" height="388" alt="image" src="https://github.com/user-attachments/assets/755dde33-c4cd-49ed-a13d-7d5f90979fb7" />

<img width="355" height="409" alt="image" src="https://github.com/user-attachments/assets/6a9c9520-6dd4-4a0b-94c4-0715741ced93" />


### 4. Przykładowa wygenerowana odpowiedź

<img width="292" height="327" alt="image" src="https://github.com/user-attachments/assets/6a3c3e16-c0ed-4752-8f41-a911abccce7d" />


### 5. Wersja robocza w Gmailu

<img width="603" height="619" alt="image" src="https://github.com/user-attachments/assets/c50a9d2e-22aa-4d4d-b7b6-b65e5adc46f2" />


## Ograniczenia

- Jakość generowanych odpowiedzi zależy od kompletności i aktualności firmowej bazy wiedzy.
- System nie ma dostępu do zewnętrznych systemów firmy, takich jak CRM, systemy rezerwacyjne czy systemy magazynowe.
- Nie potwierdza dynamicznych informacji, takich jak aktualna dostępność usług, terminy czy status zamówień, jeśli nie otrzyma odpowiednich danych.
- Nietypowe i złożone zapytania mogą wymagać dodatkowej weryfikacji przez pracownika.
- System nie obsługuje analizy załączników ani dokumentów przesyłanych przez klientów.
- Odpowiedzi generowane przez AI wymagają sprawdzenia przed wysłaniem.

Projekt ma charakter demonstracyjny i przedstawia możliwość wykorzystania AI do automatyzacji procesów związanych z obsługą klienta.

## Technologie

- Make (Integromat)
- OpenAI API
- Gmail
- Google Docs
- Webhooks / Mailhook

## Czego nauczyłem się podczas realizacji projektu

- projektowania automatyzacji procesów biznesowych,
- integracji usług Google z Make,
- wykorzystywania webhooków do uruchamiania scenariuszy,
- integracji modeli językowych przez OpenAI API,
- projektowania promptów systemowych,
- przekazywania i mapowania danych pomiędzy modułami,
- budowania systemów AI wykorzystujących zewnętrzną bazę wiedzy,
- testowania i optymalizacji przepływów automatyzacji.
