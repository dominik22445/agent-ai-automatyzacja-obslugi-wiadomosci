# Agent AI – automatyzacja obsługi wiadomości

## **Opis projektu**

System wykorzystujący sztuczną inteligencję do analizy wiadomości email, generowania odpowiedzi oraz podejmowania decyzji, czy odpowiedź wymaga weryfikacji człowieka.

Projekt wykorzystuje bazę wiedzy przechowywaną w Google Docs oraz model OpenAI do przygotowania odpowiedzi zgodnych z dostępną dokumentacją.

---

## **Problem biznesowy**

Wiele wiadomości klientów dotyczy prostych i powtarzalnych pytań, jednak część z nich wymaga indywidualnej oceny pracownika.

Projekt automatyzuje analizę wiadomości oraz rozdziela zgłoszenia na:

* możliwe do automatycznej obsługi,
* wymagające weryfikacji człowieka.

---

## **Technologie**

* Make
* OpenAI API
* Gmail
* Google Docs

---

## **Architektura rozwiązania**

Klient → Gmail → Google Docs (baza wiedzy) → OpenAI API → Gmail (draft odpowiedzi)



---

## **Funkcje**

* analiza treści wiadomości email,
* wykorzystanie bazy wiedzy zapisanej w Google Docs,
* generowanie odpowiedzi przez AI,

---

## Przykładowe działanie

### Workflow w Make

![Workflow](make-workflow.png)

### Fragment bazy wiedzy

![Baza wiedzy](knowledge-base.png)

### Początek promptu systemowego

![Początek promptu](prompt-overview.png)

### Końcówka promptu systemowego

![Końcówka promptu](prompt-classification-rules.png)

### Wynik klasyfikacji – odpowiedź automatyczna

![JSON automatyczna odpowiedź](automatic-response-result.png)

### Automatyczna odpowiedź dla klienta

![Odpowiedź automatyczna](automatic-response-email.png)

### Wynik klasyfikacji – wymagana weryfikacja

![JSON do weryfikacji](human-review-result.png)

### Odpowiedź przekazana do weryfikacji

![Odpowiedź do weryfikacji](human-review-email.png)

---

## Ograniczenia

* skuteczność odpowiedzi zależy od jakości i kompletności bazy wiedzy,
* system odpowiada wyłącznie na podstawie dostarczonych informacji i nie posiada dostępu do zewnętrznych systemów firmy,
* błędnie sformułowane lub niejednoznaczne wiadomości mogą zostać zakwalifikowane do weryfikacji przez człowieka,
* system nie potwierdza terminów, dostępności ani innych danych dynamicznych bez odpowiednich informacji wejściowych,
* odpowiedzi generowane przez AI mogą wymagać dodatkowej kontroli w przypadku nietypowych lub złożonych zapytań,
* projekt nie obsługuje załączników ani analizy dokumentów przesyłanych przez klientów,
* jakość odpowiedzi zależy od poprawności promptu oraz zdefiniowanych reguł decyzyjnych,
* projekt został przygotowany jako demonstracja wykorzystania AI do automatyzacji obsługi klienta.


---

## **Czego nauczyłem się podczas realizacji projektu**

* integracji Gmail z Make,
* wykorzystania OpenAI API w procesach biznesowych,
* budowy systemów wspierających obsługę klienta,

