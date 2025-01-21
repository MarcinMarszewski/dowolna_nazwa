1. **Jako biletomat**, chcę automatycznie aktualizować listę dostępnych biletów i ich cen, aby zapewnić zgodność z polityką przewoźnika.
1. **Jako biletomat**, chcę rejestrować wszystkie transakcje i wysyłać raporty do systemu centralnego, aby umożliwić monitoring i kontrolę operacji.
1. **Jako biletomat**, chcę posiadać czytelny ekran dotykowy, aby użytkownik mógł 
łatwo nawigować po interfejsie.
2. **Jako biletomat**, chcę być wyposażony w różne metody płatności (terminal kart, czytnik gotówki, NFC), aby obsługiwać różnorodne transakcje.
3. **Jako biletomat**, chcę wydawać resztę w gotówce, jeśli użytkownik zapłaci 
nadmiarowo, aby transakcja była zgodna z oczekiwaniami.

## Diagram przypadków użycia

```mermaid
flowchart LR
subgraph "Wybór języka"
  A@{ shape: manual-file, label: "Biletomat" }
  id1[Wyświetlenie opcji językowych]
  id2[Rejestracja wyboru języka]
  id3[Dostosowanie interfejsu]
  id4[Wyświetlenie opcji językowych]
  id5[Powrót do języka domyślnego]

  A --> id1
  A --> id2
  A --> id3
  id5-. extend .-> id1
  id5-. extend .-> id2
  id5-. extend .-> id3
  id1-. include .-> id4
  
end
subgraph "Wyświetlenie dostępnych biletów"
  B@{ shape: manual-file, label: "Biletomat" }
  id11[Uruchomienie ekranu powitalnego]
  id22[Pobranie listy biletów]
  id33[Wyświetlenie biletów]
  id44[Oczekiwanie na wybór użytkownika]
  id55[Aktualizacja biletów]
  id66[Ostrzeżenie o braku danych]

  B --> id11
  B --> id22
  B --> id33
  B --> id44
  id22-. include .-> id55
  id66-. extend .-> id22

end
subgraph "Wyświetlenie podsumowania transakcji"
  C@{ shape: manual-file, label: "Biletomat" }
  uc1[Gromadzenie danych o transakcji]
  uc2[Wyświetlenie podsumowania]
  uc3[Oczekiwanie na decyzję użytkownika]
  uc4[Obsługa anulowania]

  C --> uc1
  C --> uc2
  C --> uc3

  uc1-. include .-> uc2
  uc4-. extend .-> uc3

end
subgraph "Generowanie potwierdzenia zakupu"
  D@{ shape: manual-file, label: "Biletomat" }
  DD@{ shape: manual-file, label: "System transakcyjny" }
  DDD@{ shape: manual-file, label: "Użytkownik" }
  u1[Potwierdzenie zakończenia transakcji]
  u2[Generowanie potwierdzenia]
  u3[Informacja o potwierdzeniu]
  u4[Oczekiwanie na odbiór]
  u5[Generowanie biletu]
  u6[Błąd generowania]

  DD --> u1
  D --> u5
  D --> u2
  D --> u3
  D --> u4
  u1 --> D
  u1 --> u2
  u2 --> u3
  u3 --> u4
  u4 --> DDD

  u1-. include .-> u5
  u6-. extend .-> u2

end

```
## Wspólny diagram

```mermaid
flowchart LR
  A@{ shape: manual-file, label: "Biletomat" }
  id1[Wyświetlenie opcji językowych]
  id2[Rejestracja wyboru języka]
  id3[Dostosowanie interfejsu]
  id4[Wyświetlenie opcji językowych]
  id5[Powrót do języka domyślnego]

  id11[Uruchomienie ekranu powitalnego]
  id22[Pobranie listy biletów]
  id33[Wyświetlenie biletów]
  id44[Oczekiwanie na wybór użytkownika]
  id55[Aktualizacja biletów]
  id66[Ostrzeżenie o braku danych]

  uc1[Gromadzenie danych o transakcji]
  uc2[Wyświetlenie podsumowania]
  uc3[Oczekiwanie na decyzję użytkownika]
  uc4[Obsługa anulowania]

  u1[Potwierdzenie zakończenia transakcji]
  u2[Generowanie potwierdzenia]
  u3[Informacja o potwierdzeniu]
  u4[Oczekiwanie na odbiór]
  u5[Generowanie biletu]
  u6[Błąd generowania]

  A --> id1
  A --> id2
  A --> id3
  id5-. extend .-> id1
  id5-. extend .-> id2
  id5-. extend .-> id3
  id1-. include .-> id4

  A --> id11
  A --> id22
  A --> id33
  A --> id44
  id22-. include .-> id55
  id66-. extend .-> id22

  A --> uc1
  A --> uc2
  A --> uc3

  uc1-. include .-> uc2
  uc4-. extend .-> uc3

  A --> u1
  A --> u2
  A --> u3
  A --> u4

  u1-. include .-> u5
  u6-. extend .-> u3
```
