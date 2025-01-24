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
flowchart LR
  A@{ shape: manual-file, label: "Użytkownik" }
  id1[Rozpoczęcie interakcji]
  id2[Sprawdzenie biletów]
  id3[Anulowanie transakcji]
  id4[Wyświetlenie podpowiedzi interfejsu]
  id11[Wybranie kategorii]
  id111[Wybranie biletu]
  id1111[Potwierdzenie wyboru]

  id5[Wybranie języka]
  id6[Ustawienie domyślnego języka]
  id8[Wyświetlenie listy popularnych języków]
  id22[Rozpoczęcie interakcji]
  id222[Wyświetlenie opcji języka]
  id2222[Dostosowanie interfejsu]

  uc1[Wybór biletu i płatności]
  uc2[Wyświetlenie podsumowania]
  uc3[Potwierdzenie lub cofnięcie]
  uc4[Kontynuacja lub anulowanie]
  uc7[Ostrzeżenie o błędzie]

  u1[Generowanie potwierdzenia]
  u2[Odebranie potwierdzenia]
  u3[Komunikat o zakończeniu]
  u5[Generowanie biletu]
  u6[Wybór formy potwierdzenia]

  A --> id1
  A --> id11
  A --> id111
  A --> id1111
  id1-. include .-> id3
  id11-. include .-> id3
  id111-. include .-> id3
  id1111-. include .-> id3
  id111-. include .-> id2
  id4-. extend .-> id11
  id4-. extend .-> id111

  A --> id5;
  A --> id22;
  A --> id222;
  A --> id2222;
  id5-. include .-> id3
  id22-. include .-> id3
  id222-. include .-> id3
  id2222-. include .-> id3
  id2222-. include .-> id6
  id8-. extend .-> id222

  A --> uc1
  A --> uc3
  A --> uc4
  uc1-. include .-> id3
  uc2-. include .-> id3
  uc3-. include .-> id3
  uc4-. include .-> id3
  uc1-. include .-> uc2
  uc7-. extend .-> uc1

  A --> u1
  A --> u2
  A --> u3
  u1-. include .-> id3
  u2-. include .-> id3
  u3-. include .-> id3
  u1-. include .-> u5
  u6-. extend .-> u1
```

# Diagramy sekwencji

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
 
## Wizualizacja diagramu sekwencji

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

## Wizualizacja diagramu sekwencji

```mermaid
sequenceDiagram
  actor user as Użytkownik
  participant ui as Interfejs biletomatu
  participant sys as System biletomatu

  user->>ui: Zakończenie transakcji
  ui->>sys: Zakończenie transakcji
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
