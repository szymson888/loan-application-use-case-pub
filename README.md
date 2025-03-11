# Podsumowanie Repozytorium – System Pożyczek
Repozytorium zawiera kompletną dokumentację i przykłady implementacji systemu obsługującego proces udzielania pożyczek. Celem projektu jest stworzenie przejrzystego materiału edukacyjnego dla pracowników, 
który jednocześnie prezentuje przykładową architekturę opartą na mikroserwisach i REST API.
Repozytorium jest utrzymywane przez firmę AGIDOT sp. z o.o. https://agidot.eu/

## Główne Założenia Systemu
System umożliwia kompleksową obsługę wniosku o udzielenie pożyczki, dzieląc proces na kilka kluczowych etapów, z których każdy jest realizowany przez dedykowany serwis. Podejście to pozwala na łatwe skalowanie, modyfikację poszczególnych elementów oraz lepsze zrozumienie zasad działania architektury opartej na serwisach.

## Kluczowe Serwisy
### Weryfikacja Osoby Prywatnej

Opis: Usługa odpowiedzialna za wstępną weryfikację danych wnioskodawcy.
Przykładowe dane wejściowe: Imię, nazwisko, PESEL, numer dowodu osobistego oraz wiek.
Odpowiedź: Unikalny identyfikator autoryzacji oraz informacja, czy wnioskodawca został pozytywnie autoryzowany.
{
  "wnioskodawca": 
  {
    "imie": "Jan",
    "nazwisko": "Kowalski",
    "pesel": "12345612345",
    "dowod": "abc1234",
    "wiek": 34
    }
    { 
  “imię”: “Maria”,
  “Nazwisko”: “Warzecha”,
  “Pesel”: “1212121344”,
 “Dowod”: “xyz3344”,
“Wiek”: “28”
}
{
“imię”: “Anna”,
  “Nazwisko”: “Nowak”,
  “Pesel”: “5436542356”,
 “Dowod”: “qwe2345”,
“Wiek”: “52”
}
  },
### Ocena Ryzyka

Opis: Serwis, który dokonuje analizy ryzyka kredytowego na podstawie statusu zatrudnienia, formy zatrudnienia oraz dokładnych danych o dochodach.
Logika decyzyjna:
Umowa o pracę i dochody powyżej 4000zł – scoring A
Umowa o pracę i dochody w przedziale 2500-4000zł – scoring B
Inne kombinacje warunków wpływają na przydzielenie scoringu od D do E
Odpowiedź: Wynik scoringowy (A, B, C, D lub E).


### Dopasowanie Produktów

Opis: Na podstawie przyznanego scoringu system wyszukuje i przedstawia listę dopasowanych produktów pożyczkowych.
Przykładowe mapowanie:
Kredyt hipoteczny powyżej 500 000zł – scoring A
Kredyt konsumencki do 40 000zł – scoring C
Karta kredytowa – scoring D
Szybka pożyczka – scoring E


### Złożenie Wniosku Kredytowego

Opis: Finalizacja procesu poprzez potwierdzenie danych oraz formalne złożenie wniosku.
Przykładowy request: Potwierdzenie danych poprzez wpisanie "TAK".
Odpytanie o Status Wniosku

Opis: Umożliwia sprawdzenie aktualnego statusu wniosku (np. pozytywny, negatywny, do poprawy).


## Odpytanie o Numer Umowy

Opis: Pozwala na uzyskanie informacji dotyczącej numeru umowy kredytowej po pozytywnej weryfikacji wniosku.


## Podsumowanie Funkcjonalności
Modularność: Każdy serwis realizuje określone zadanie, co ułatwia utrzymanie i rozwój systemu.
Przykłady Implementacji: Repozytorium zawiera przykłady zapytań i odpowiedzi dla poszczególnych punktów procesu, co ułatwia zrozumienie przepływu danych między serwisami.
Elastyczność: System przewiduje możliwość rozbudowy i modyfikacji – np. zmiana logiki oceny ryzyka czy dodanie nowych typów produktów.
Praktyczne Zastosowanie: Dokumentacja ma służyć jako materiał szkoleniowy, pokazujący zastosowanie nowoczesnych rozwiązań architektonicznych w praktyce biznesowej.
