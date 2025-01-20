## User Stories

1. **Jako użytkownik**, chcę szybko wybrać rodzaj biletu, aby zminimalizować czas spędzony przy biletomacie.
1. **Jako użytkownik**, chcę mieć możliwość wyboru języka, aby móc korzystać z biletomatu bez względu na znajomość języka lokalnego.
1. **Jako użytkownik**, chcę sprawdzić poprawność transakcji przed jej finalizacją, aby uniknąć pomyłek.
1. **Jako użytkownik**, chcę otrzymać potwierdzenie zakupu (np. wydruk biletu lub elektroniczny bilet), aby móc korzystać z transportu zgodnie z przepisami.
1. **Jako użytkownik**, chcę płacić za bilet kartą, gotówką lub telefonem, aby mieć większą elastyczność w wyborze metody płatności.
2. **Jako użytkownik**, chcę otrzymać wyraźne instrukcje na ekranie, aby wiedzieć, jak dokonać zakupu krok po kroku.
3. **Jako użytkownik**, chcę widzieć czas pozostały na decyzję (np. wyświetlany 
licznik czasu), aby móc szybko podjąć działanie.

## Diagramy przypadków użycia

```mermaid
flowchart LR
subgraph "Szybki wybór rodzaju biletu"
  A@{ shape: manual-file, label: "Użytkownik" }
  id1[Rozpoczęcie interakcji]
  id2[Sprawdzenie biletów]
  id3[Anulowanie transakcji]
  id4[Wyświetlenie podpowiedzi interfejsu]
  id11[Wybranie kategorii]
  id111[Wybranie biletu]
  id1111[Potwierdzenie wyboru]

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
  
end
subgraph "Wybór języka"
  B@{ shape: manual-file, label: "Użytkownik" }
  id5[Wybranie języka]
  id6[Ustawienie domyślnego języka]
  id7[Anulowanie transakcji]
  id8[Wyświetlenie listy popularnych języków]
  id22[Rozpoczęcie interakcji]
  id222[Wyświetlenie opcji języka]
  id2222[Dostosowanie interfejsu]

  B --> id5;
  B --> id22;
  B --> id222;
  B --> id2222;
  id5-. include .-> id7
  id22-. include .-> id7
  id222-. include .-> id7
  id2222-. include .-> id7
  id2222-. include .-> id6
  id8-. extend .-> id222
  



end
```

### Wspólny diagram przypadków użycia

```mermaid
flowchart LR
  A@{ shape: manual-file, label: "Użytkownik" }
  id1[Szybki wybór rodzaju biletu]
  id2[Sprawdzenie biletów]
  id3[Anulowanie transakcji]
  id4[Podpowiedź interfejsu]

  A --> id1
  id1-- include ---id2
  id1-- include ---id3
  id4-- extend ---id1
  A --> id5;
  id5[Wybór języka] --include--> id6;
  id5 --include--> id3;
  id8 --extend--> id5;
  id6[Domyślny język];
  id8[Lista popularnych języków];
```
