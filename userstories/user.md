# User Stories

1. **Jako użytkownik**, chcę szybko wybrać rodzaj biletu, aby zminimalizować czas spędzony przy biletomacie.
1. **Jako użytkownik**, chcę mieć możliwość wyboru języka, aby móc korzystać z biletomatu bez względu na znajomość języka lokalnego.
1. **Jako użytkownik**, chcę sprawdzić poprawność transakcji przed jej finalizacją, aby uniknąć pomyłek.
1. **Jako użytkownik**, chcę otrzymać potwierdzenie zakupu (np. wydruk biletu lub elektroniczny bilet), aby móc korzystać z transportu zgodnie z przepisami.
1. **Jako użytkownik**, chcę płacić za bilet kartą, gotówką lub telefonem, aby mieć większą elastyczność w wyborze metody płatności.
2. **Jako użytkownik**, chcę otrzymać wyraźne instrukcje na ekranie, aby wiedzieć, jak dokonać zakupu krok po kroku.
3. **Jako użytkownik**, chcę widzieć czas pozostały na decyzję (np. wyświetlany 
licznik czasu), aby móc szybko podjąć działanie.

# Diagramy przypadków użycia

## 1. Szybki wybór rodzaju biletu
```mermaid
graph TD
  D@{ shape: manual-file, label: "Użytkownik" }
  u1[Rozpoczęcie interakcji]
  u2[Wybór kategorii]
  u3[Wybór biletu]
  u4[Wyświetlenie podsumowania]
  u5[Potwierdzenie wyboru]
  u6[Anulowanie transakcji]
  u7[Sprawdzenie biletów]
  u8[Podpowiedź interfejsu]

  D --> u1
  u1 --> u2
  u2 --> u3
  u3 --> u4
  u4 --> u5

  u1-. include .-> u6
  u2-. include .-> u6
  u3-. include .-> u6
  u4-. include .-> u6
  u5-. include .-> u6
  u3-. include .-> u7
  u8-. extend .-> u2
  u8-. extend .-> u3

subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
  u6
  u7
  u8
end

```

## 2. Wybór języka

```mermaid
graph TD
  US@{ shape: manual-file, label: "Użytkownik" }
  uc1[Rozpoczęcie interakcji]
  uc2[Wyświetlenie opcji języka]
  uc3[Wybór języka]
  uc4[Dostosowanie interfejsu]
  uc5[Anulowanie transakcji]
  uc6[Ustawienie domyślnego języka]
  uc7[Wyświetlenie listy popularnych języków]

  US  --> uc1
  uc1 --> uc2
  uc2 --> uc3
  uc3 --> uc4

  uc1 -. include .-> uc5
  uc2 -. include .-> uc5
  uc3 -. include .-> uc5
  uc4 -. include .-> uc5
  uc6 -. extend .-> uc2
  uc2 -. include .-> uc7

subgraph Biletomat
  uc1
  uc2
  uc3
  uc4
  uc5
  uc6
  uc7
end

```


## 3. Sprawdzenie poprawności transakcji
```mermaid
graph TD
  US@{ shape: manual-file, label: "Użytkownik" }
  TS@{ shape: manual-file, label: "System transakcyjny" }
  uc1[Wybór biletu i płatności]
  uc2[Wyświetlenie podsumowania]
  uc3[Potwierdzenie lub cofnięcie]
  uc4[Kontynuacja lub anulowanie]
  uc5[Anulowanie transakcji]
  uc6[Ostrzeżenie o błędzie]
  uc7[Podsumowanie transakcji]

  US  --> uc1
  uc1 --> uc2
  uc2 --> uc3
  uc3 --> uc4
  uc4 --> TS

  uc1 -. include .-> uc5
  uc2 -. include .-> uc5
  uc3 -. include .-> uc5
  uc4 -. include .-> uc5
  uc6 -. extend .-> uc2
  uc2 -. include .-> uc7

subgraph Biletomat
  uc1
  uc2
  uc3
  uc4
  uc5
  uc6
  uc7
end

```

## 4. Otrzymanie potwierdzenia zakupu
```mermaid
graph TD
  D@{ shape: manual-file, label: "Użytkownik" }
  u1[Generowanie potwierdzenia]
  u2[Odebranie potwierdzenia]
  u3[Komunikat o zakończeniu]
  u4[Anulowanie transakcji]
  u5[Generowanie biletu]
  u6[Wybór formy potwierdzenia]

  D --> u1
  u1 --> u2
  u2 --> u3

  u1-. include .-> u5
  u1-. include .-> u4
  u2-. include .-> u4
  u3-. include .-> u4
  u6-. extend .-> u1


subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
  u6
end

```

### Wspólny diagram przypadków użycia

```mermaid
graph TD

D@{ shape: manual-file, label: "Użytkownik" }
  u1[Rozpoczęcie interakcji]
  u2[Wybór kategorii]
  u3[Wybór biletu]
  u4[Wyświetlenie podsumowania]
  u5[Potwierdzenie wyboru]
  u6[Anulowanie transakcji]
  u7[Sprawdzenie biletów]
  u8[Podpowiedź interfejsu]

  D --> u1
  u1 --> u2
  u2 --> u3
  u3 --> u4
  u4 --> u5

  u1-. include .-> u6
  u2-. include .-> u6
  u3-. include .-> u6
  u4-. include .-> u6
  u5-. include .-> u6
  u3-. include .-> u7
  u8-. extend .-> u2
  u8-. extend .-> u3

  uc1[Rozpoczęcie interakcji]
  uc2[Wyświetlenie opcji języka]
  uc3[Wybór języka]
  uc4[Dostosowanie interfejsu]
  uc6[Ustawienie domyślnego języka]
  uc7[Wyświetlenie listy popularnych języków]

  D  --> uc1
  uc1 --> uc2
  uc2 --> uc3
  uc3 --> uc4

  uc1 -. include .-> u6
  uc2 -. include .-> u6
  uc3 -. include .-> u6
  uc4 -. include .-> u6
  uc6 -. extend .-> uc2
  uc2 -. include .-> uc7

  w1[Wybór biletu i płatności]
  w2[Wyświetlenie podsumowania]
  w3[Potwierdzenie lub cofnięcie]
  w4[Kontynuacja lub anulowanie]
  w6[Ostrzeżenie o błędzie]
  w7[Podsumowanie transakcji]

  D  --> w1
  w1 --> w2
  w2 --> w3
  w3 --> w4

  w1 -. include .-> u6
  w2 -. include .-> u6
  w3 -. include .-> u6
  w4 -. include .-> u6
  w6 -. extend .-> w2
  w2 -. include .-> w7

  x1[Generowanie potwierdzenia]
  x2[Odebranie potwierdzenia]
  x3[Komunikat o zakończeniu]
  x5[Generowanie biletu]
  x6[Wybór formy potwierdzenia]

  D --> x1
  x1 --> x2
  x2 --> x3

  x1-. include .-> x5
  x1-. include .-> u6
  x2-. include .-> u6
  x3-. include .-> u6
  x6-. extend .-> x1

  subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
  u6
  u7
  u8

  uc1
  uc2
  uc3
  uc4
  uc6
  uc7

  w1
  w2
  w3
  w4
  w6
  w7

  x1
  x2
  x3
  x5
  x6
  end
```

# Diagramy sekwencji

## Diagram sekwencji dla przypadku użycia Szybki wybór rodzaju biletu

- Aktor: Użytkownik
- Obiekty: Interfejs biletomatu, System biletomatu, System transakcyjny
- Kolejność komunikatów:
  1. Użytkownik klika w dowolne miejsce w biletomacie
  2. Interfejs wyświetla okno wyboru kategorii biletu
  1. Użytkownik wybiera kategorię biletu
  2. Interfejs pobiera listę dostępnych biletów
  3. Interfejs wyświetla listę biletów
  4. Użytkownik wybiera bilet
  5. Interfejs wyświetla podsumowanie
  6. Użytkownik potwierdza wybór
- Scenariusz alternatywny 1 (Cofnięcie  wyboru)
  1. Użytkownik klika w dowolne miejsce w biletomacie
  2. Interfejs wyświetla okno wyboru kategorii biletu
  1. Użytkownik wybiera kategorię biletu
  2. Interfejs pobiera listę dostępnych biletów
  3. Interfejs wyświetla listę biletów
  4. Użytkownik wybiera bilet
  5. Interfejs wyświetla podsumowanie
  6. Użytkownik anuluje wybór
  7. Interfejs wyświetla ekran główny
- Scenariusz alternatywny 2 (Długie oczekiwanie)
  1. Użytkownik klika w dowolne miejsce w biletomacie
  2. Interfejs wyświetla okno wyboru kategorii biletu
  3. Użytkownik długo oczekuje
  4. Interfejs wyświetla podpowiedź
  1. Użytkownik wybiera kategorię biletu
  2. Interfejs pobiera listę dostępnych biletów
  3. Interfejs wyświetla listę biletów
  3. Użytkownik długo oczekuje
  4. Interfejs wyświetla podpowiedź
  5. Użytkownik wybiera bilet
  6. Interfejs wyświetla podsumowanie
  7. Użytkownik potwierdza wybór

```mermaid
sequenceDiagram
  actor user as Użytkownik
  participant ui as Interfejs biletomatu
  participant sys as System biletomatu

  user->>ui: Rozpoczęcie kupna biletu
  ui->>user: Wyświetlenie okna wyboru kategorii
  user-->>ui: Kategoria lub minięcie czasu

  OPT Użytkownik długo wybiera
    ui->>user: Wyświetlenie podpowiedzi
    user-->>ui: Kategoria
  END
  ui->>sys: Pobranie dostępnych biletów
  sys-->>ui: Dostępne bilety

  ui->>user: Wyświetlenie okna wyboru biletu
  user-->>ui: Bilet lub minięcie czasu

  OPT Użytkownik długo wybiera
    ui->>user: Wyświetlenie podpowiedzi
    user-->>ui: Bilet
  END

  ui->>user: Wyświetlenie podsumowania
  user-->>ui: Wybranie opcji

  ALT Potwierdzenie wyboru
    ui->>sys: Realizacja tranzakcji
    sys-->>ui: return
    ui-->>user: return
  ELSE Cofnięcie wyboru
    ui-->>user: Zakończenie kupna biletu
  END
```

## Diagram sekwencji dla przypadku użycia wybrania języka

- Aktor: Użytkownik
- Obiekty: Interfejs biletomatu, System biletomatu
- Kolejność komunikatów:
  1. Użytkownik klika w dowolne miejsce na interfejsie biletomatu
  2. Interfejs biletomatu pobiera dostępne języki z systemu
  3. Interfejs biletomatu wyświetla ekran powitalny z opcjami wyboru języka
  4. Użytkownik wybiera preferowany język
  5. System biletomatu dostosowuje interfejs do wybranego języka
  6. Interfejs biletomatu wyświetla dostosowany interfejs
- Scenariusz alternatywny 1 (Lista popularnych języków)
  1. Użytkownik klika w dowolne miejsce na interfejsie biletomatu
  2. Interfejs biletomatu pobiera dostępne języki z systemu
  3. Interfejs biletomatu wyświetla ekran powitalny z opcjami wyboru języka
  4. Użytkownik wciska przycisk popularnych języków
  5. Interfejs wyświetla listę popularnych języków
  6. Użytkownik wybiera preferowany język
  7. System biletomatu dostosowuje interfejs do wybranego języka
  8. Interfejs biletomatu wyświetla dostosowany interfejs

```mermaid
sequenceDiagram
  actor user as Użytkownik
  participant ui as Interfejs biletomatu
  participant sys as System biletomatu

  user->>ui: Rozpoczęcie interakcji
  ui->>sys: Pobranie dostępnych języków
  sys-->>ui: Dostępne języki
  ui-->>user: Wyświetlenie ekranu powitalnego z opcjami wyboru języka

  opt Popularne języki
    user->>ui: Wybranie przycisku popularnych jezyków
    ui-->>user: Wyświetlenie okna popularnych języków
  end

  user->>ui: Wybór języka
  ui->>sys: Dostosowanie interfejsu do języka
  sys-->>ui: return
  ui-->>user: Wyświetlenie dostosowanego interfejsu

  
```

## Diagram sekwencji dla przypadku użycia sprawdzenia poprawności transakcji

- Aktor: Użytkownik
- Obiekty: Interfejs biletomatu, System biletomatu, System transakcyjny
- Kolejność komunikatów:
  1. Użytkownik wybiera bilety i metodę płatności
  2. System biletomatu weryfikuje poprawność wyboru
  4. Interfejs biletomatu wyświetla podsumowanie transakcji
  5. Użytkownik sprawdza szczegóły i potwierdza wybór
  6. System biletomatu zapisuje dane transakcji
  7. System transakcyjny dokonuje transakcji
- Scenariusz alternatywny 1 (Niepoprawny wybór)
  1. Użytkownik wybiera bilety i metodę płatności
  2. System biletomatu wykrywa niepoprawny wybór
  4. Interfejs biletomatu wyświetla ostrzeżenie o błędnym wyborze
  5. Użytkownik poprawia wybór
  2. System biletomatu weryfikuje poprawność wyboru
  4. Interfejs biletomatu wyświetla podsumowanie transakcji
  5. Użytkownik sprawdza szczegóły i potwierdza wybór
  6. System biletomatu zapisuje dane transakcji
  7. System transakcyjny dokonuje transakcji
  8. Interfejst biletomatu wyświetla ekran pożegnania
- Scenariusz alternatywny 2 (Cofnięcie wyboru)
  1. Użytkownik wybiera bilety i metodę płatności
  2. System biletomatu weryfikuje poprawność wyboru
  4. Interfejs biletomatu wyświetla podsumowanie transakcji
  5. Użytkownik sprawdza szczegóły i cofa wybór
  6. Interfejs biletomatu wyświetla ekran wyboru biletów i metody płatności

```mermaid
sequenceDiagram
  actor user as Użytkownik
  participant ui as Interfejs biletomatu
  participant sys as System biletomatu
  participant tsys as System transakcyjny

  user->>ui: Wybór biletów i metody płatności
  ui->>sys: Sprawdzenie poprawności wyboru
  sys-->>ui: Wynik sprawdzenia

  LOOP Dopóki wybór niepoprawny
    ui->>user: Wyświetlenie ostrzeżenia o błędnym wyborze
    user-->>ui: Poprawienie wyboru
    ui->>sys: Sprawdzenie poprawności wyboru
    sys-->>ui: Wynik sprawdzenia
  END

  ui-->>user: Wyświetlenie podsumowania transakcji



  ALT Potwierdzenie wyboru
    user->>ui: Potwierdzenie wyboru
    ui->>sys: Zapisanie danych
    sys->>tsys: Wykonanie transakcji
    tsys-->>sys: return
    sys-->>ui: return
    ui-->>user: Wyświetlenie ekranu pożegnania
  ELSE Cofnięcie wyboru
    user->>ui: Cofnięcie wyboru
    ui-->>user: Wyświetlenie ekranu wyboru biletów i metody płatności
  END
```

## Diagram sekwencji dla przypadku użycia Otrzymanie potwierdzenia zakupu

- Aktor: Użytkownik
- Obiekty: Interfejs biletomatu, System biletomatu
- Kolejność komunikatów:
  1. Użytkownik kończy transakcję
  1. System generuje potwierdzenie
  2. Interfejs wyświetla okno wyboru rodzaju potwierdzenia
  3. Użytkownik wybiera potwierdzenie elektroniczne
  4. Interfejs wysyła informację o potwierdzeniu elektronicznym
  5. System wysyła potwierdzenie elektroniczne użytkownikowi
  6. Interfejs wyświetla informację o zakończeniu procesu
- Scenariusz alternatywny 1 (Wybór potwierdzenia drukowanego)
  1. Użytkownik kończy transakcję
  1. System generuje potwierdzenie
  2. Interfejs wyświetla okno wyboru rodzaju potwierdzenia
  3. Użytkownik wybiera potwierdzenie drukowane
  4. Interfejs wysyła informację o potwierdzeniu drukowanym
  5. System wysyła potwierdzenie do intefejsu
  6. Interfejs drukuje potwierdzenie
  7. Użytkownik odbiera potiwerdzenie
  8. Interfejs wyświetla informację o zakończeniu procesu

```mermaid
sequenceDiagram
  actor user as Użytkownik
  participant ui as Interfejs biletomatu
  participant sys as System biletomatu
  user->>ui: Zakończenie transakcji
  ui->>sys: Zakończenie transakcji
  sys->>sys: Generowanie potwierdzenia
  sys-->>ui: return
  ui->>user: Okno wyboru rodzaju potwierdzenia

  user-->>ui: Wybrany rodzaj potwierdzenia

  alt Potwierdzenie Elektroniczne
    ui->>sys: Żądanie potwierdzenia elektronicznego
    sys->>sys: Wysłanie potwierdzenia elektronicznego
    sys-->>ui: return
  else Potwierdzenie Drukowane
    ui->>sys: Pobranie potwierdzenia do druku
    sys-->>ui: Potwierdzenie
    ui->>user: Wydrukowanie potwierdzenie
    user-->>ui: Odebranie potwierdzenia
  end

  ui->>user: Wyświetlenie informacji o zakończeniu procesu
  user-->>ui: return
  ui-->>user: return
```

# Diagramy klas

## Opis klas dla przypadku użycia "Szybki wybór rodzaju biletu"
### Klasy
#### TicketMachineTicketView
- Atrybuty: `List<TicketCategory> ticketCategories`, `List<Ticket> availableTickets`, `Timer hintTimer`
- Metody: `void showHint()`, `void showCategorySelectionWindow()`, `void showTicketSelectionWindow()`, `void showSummary()`, `void chooseCategory()`, `void chooseTicket(Ticket chosenTicket)`, `void chooseSummary(Boolean chosenOption)`

#### TicketService
- Atrybuty: `List<Ticket> tickets`
- Metody: `List<Ticket> getTickets()`, `List<TicketCategory> getCategories()`, `void cancelTransaction()`, `void continueTransaction()`

#### Ticket
- Atrybuty: `TicketCategory category`, `String name`
#### TicketCategory
- Atrybuty: `String name`

### Relacje:
- `TicketMachineTicketView` powiązany z `TicketService` (Asocjacja)
- `Ticket` powiązany z `TicketCategory` (Asocjacja)

## WIZUALIZACJA DIAGRAMU KLAS

```mermaid
classDiagram
  class TicketMachineTicketView {
    - List&lt;TicketCategory> ticketCategories
    - List&lt;Ticket> availableTickets
    - Timer hintTimer

    + void showHint()
    + void showCategorySelectionWindow()
    + void showTicketSelectionWindow()
    + void showSummary()

    + void chooseCategory(Category chosenCategory)
    + void chooseTicket(Ticket chosenTicket)
    + void chooseSummary(Boolean chosenOption)
  }

  class TicketService {
    - List&lt;Ticket> tickets
    + List&lt;Ticket> getTickets()
    + List&lt;TicketCategory> getCategories()
    + void cancelTransaction()
    + void continueTransaction()
  }

  class Ticket {
    - String name
  }

  class TicketCategory {
    - String name
  }

  TicketService <-- TicketMachineTicketView : Wyświetla Dane
  TicketCategory --> Ticket : Opisuje
```

## Opis klas dla przypadku użycia "Wybór języka"
### Klasy
#### TicketMachineLanguageChangeView
- Atrybuty: `List&lt;Language> languages`, `Language defaultLanguage`
- Metody: `void showAvailableLanguageOptions()`, `void showPopularLanguageOptions()`, `void setNewLanguage(Language)`, `void cancelSettingNewLanguage()`, `void setDefaultLanguage()`

#### TicketMachineMainView
- Metody: `void showLanguageChangeView()`

#### LanguageService
- Atrybuty: `List&lt;Language> languages`
- Metody: `List&lt;Language> getAvailableLanguages()`, `void setSessionLanguage()`

### Relacje:
- `TicketMachineView` powiązany z `TicketMachineLanguageChangeView` (Asocjacja)
- `LanguageService` powiązany z `TicketMachineLanguageChangeView` (Asocjacja)

## WIZUALIZACJA DIAGRAMU KLAS
```mermaid
classDiagram
  class Language {
  - string Name
  }

  class TicketMachineMainView {
    + void showLanguageChangeView()
  }

  class TicketMachineLanguageChangeView {
    - List&lt;Language> languages
    - Language defaultLanguage
    + void showAvailableLanguageOptions()
    + void showPopularLanguageOptions()
    + void setDefaultLanguage()
    + void setNewLanguage(Language)
    + void cancelSettingNewLanguage()
  }

  class LanguageService {
    - List&lt;Language> languages
    + List&lt;Language> getAvailableLanguages()
    + void setSessionLanguage()
  }

  TicketMachineMainView --> TicketMachineLanguageChangeView : Wywołuje
  TicketMachineLanguageChangeView --> LanguageService : Wyświetla dane
```

## Opis klas dla przypadku użycia "Otrzymanie potwierdzenia zakupu"
### Klasy
#### TicketMachineSaleConfirmView
- Atrybuty: `TransactionDetails details`
- Metody: `void showConfirmationMessage(TransactionDetails)`, `void showConfirmationTypeWindow()`, `void chooseConfirmationType(boolean isElectronic)`, `void chooseEndTransaction()`

#### TicketService
- Metody: `void printConfirmation(TransactionDetails details)`, `void generateTicket(Ticket ticket)`

#### TransactionService
- Metody: `void GenerateElectronicConfirmation(TransactionDetails details)`, `void GeneratePrintedConfirmation(TransactionDetails details)`, `void endTransaction()`

#### TransactionDetails
- Atrybuty: `DateTime date`, `Long id`, `List<Ticket> tickets`, `String paymentMethod`, `Double totalCost`

#### Ticket
- Atrybuty: `String name`, `Double cost`

### Relacje:
- `TransactionDetails` połączone z `TransactionService` (Asocjacja)
- `TicketService` połączone z `TransactionService` (Asocjacja)
- `TicketMachineSaleConfirmView` połączone z `TicketService` (Asocjacja)

## WIZUALIZACJA DIAGRAMU KLAS
```mermaid
classDiagram
  class TicketMachineSaleConfirmView {
    - TransactionDetails details
    + void showConfirmationMessage(TransactionDetails details)
    + void showConfirmationTypeWindow()
    + void chooseConfirmationType(boolean isElectronic)
    + void chooseEndTransaction();
  }

  class TicketService {
    + void printConfirmation(TransactionDetails details)
    + void generateTicket(Ticket ticket)
  }

  class TransactionService {
    + void GenerateElectronicConfirmation(TransactionDetails details)
    + void GeneratePrintedConfirmation(TransactionDetails details)
    + void endTransaction()
  }

  class TransactionDetails {
    - DateTime date
    - Long id
    - List<Ticket> tickets
    - String paymentMethod
    - Double totalCost
  }

  TicketMachineSaleConfirmView <-- TicketService : Obsługuje
  TicketService <-- TransactionService : Obsługuje
```
