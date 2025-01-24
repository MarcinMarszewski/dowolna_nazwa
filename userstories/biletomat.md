# User Stories

1. **Jako biletomat**, chcę automatycznie aktualizować listę dostępnych biletów i ich cen, aby zapewnić zgodność z polityką przewoźnika.
1. **Jako biletomat**, chcę rejestrować wszystkie transakcje i wysyłać raporty do systemu centralnego, aby umożliwić monitoring i kontrolę operacji.
1. **Jako biletomat**, chcę posiadać czytelny ekran dotykowy, aby użytkownik mógł 
łatwo nawigować po interfejsie.
2. **Jako biletomat**, chcę być wyposażony w różne metody płatności (terminal kart, czytnik gotówki, NFC), aby obsługiwać różnorodne transakcje.
3. **Jako biletomat**, chcę wydawać resztę w gotówce, jeśli użytkownik zapłaci 
nadmiarowo, aby transakcja była zgodna z oczekiwaniami.

# Diagramy przypadków użycia

## 1. "Wyświetlenie dostępnych biletów"
```mermaid
graph TD
  D@{ shape: manual-file, label: "Użytkownik" }
  u1[Uruchomienie ekranu powitalnego]
  u2[Pobranie listy biletów]
  u3[Wyświetlenie biletów]
  u4[Oczekiwanie na wybór użytkownika]
  u5[Aktualizacja biletów]
  u6[Ostrzeżenie o braku danych]

  D --> u1
  u1 --> u2
  u2 --> u3
  u3 --> u4

  u2-. include .-> u5
  u6-. extend .-> u3

subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
  u6
end

```

## 2. "Wybór języka"


```mermaid
graph TD
  DDD@{ shape: manual-file, label: "Użytkownik" }

  u1[Wyświetlenie opcji językowych]
  u2[Rejestracja wyboru języka]
  u3[Dostosowanie interfejsu]
  u4[Wyświetlenie opcji językowych]
  u5[Powrót do języka domyślnego]

  DDD --> u1
  u1 --> u2
  u2 --> u3

  u1-. include .-> u4
  u5-. extend .-> u2

subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
end

```

## 3. "Wyświetlenie podsumowania transakcji"

```mermaid
graph TD
  DDD@{ shape: manual-file, label: "Użytkownik" }

  u1[Gromadzenie danych i transakcji]
  u2[Wyświetlenie podsumowania]
  u3[Oczekiwanie na decyzję użytkownika]
  u4[Podsumowanie transakcji]
  u5[Obsługa anulowania]

  DDD --> u1
  u1 --> u2
  u2 --> u3

  u2-. include .-> u4
  u5-. extend .-> u3

subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
end

```

## 4. "Generowanie potwierdzenia zakupu"

```mermaid
graph TD
  DD@{ shape: manual-file, label: "System transakcyjny" }
  DDD@{ shape: manual-file, label: "Użytkownik" }
  u1[Potwierdzenie zakończenia transakcji]
  u2[Generowanie potwierdzenia]
  u3[Informacja o potwierdzeniu]
  u4[Oczekiwanie na odbiór]
  u5[Generowanie biletu]
  u6[Powiadomienie o błędzie generowania]

  DD --> u1
  u1 --> u2
  u2 --> u3
  u3 --> u4
  u4 --> DDD

  u1-. include .-> u5
  u6-. extend .-> u2

subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
  u6
end

```
# Wspólny diagram przypadków użycia

```mermaid
graph TD
  D@{ shape: manual-file, label: "Użytkownik" }
  u1[Uruchomienie ekranu powitalnego]
  u2[Pobranie listy biletów]
  u3[Wyświetlenie biletów]
  u4[Oczekiwanie na wybór użytkownika]
  u5[Aktualizacja biletów]
  u6[Ostrzeżenie o braku danych]

  D --> u1
  u1 --> u2
  u2 --> u3
  u3 --> u4

  u2-. include .-> u5
  u6-. extend .-> u3

  x1[Wyświetlenie opcji językowych]
  x2[Rejestracja wyboru języka]
  x3[Dostosowanie interfejsu]
  x4[Wyświetlenie opcji językowych]
  x5[Powrót do języka domyślnego]

  D --> x1
  x1 --> x2
  x2 --> x3

  x1-. include .-> x4
  x5-. extend .-> x2

  y1[Gromadzenie danych i transakcji]
  y2[Wyświetlenie podsumowania]
  y3[Oczekiwanie na decyzję użytkownika]
  y4[Podsumowanie transakcji]
  y5[Obsługa anulowania]

  D --> y1
  y1 --> y2
  y2 --> y3

  y2-. include .-> y4
  y5-. extend .-> y3

  DD@{ shape: manual-file, label: "System transakcyjny" }
  z1[Potwierdzenie zakończenia transakcji]
  z2[Generowanie potwierdzenia]
  z3[Informacja o potwierdzeniu]
  z4[Oczekiwanie na odbiór]
  z5[Generowanie biletu]
  z6[Powiadomienie o błędzie generowania]

  DD --> z1
  z1 --> z2
  z2 --> z3
  z3 --> z4
  z4 --> D

  z1-. include .-> z5
  z6-. extend .-> z2


subgraph Biletomat
  u1
  u2
  u3
  u4
  u5
  u6

  x1
  x2
  x3
  x4
  x5

  y1
  y2
  y3
  y4
  y5

  z1
  z2
  z3
  z4
  z5
  z6
end



  

```
