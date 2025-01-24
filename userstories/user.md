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
