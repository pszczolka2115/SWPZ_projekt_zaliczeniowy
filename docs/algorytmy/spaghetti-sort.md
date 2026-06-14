# Spaghetti Sort

## Opis

Spaghetti Sort (znany też jako *Poll's algorithm*, *Spaghetti stack sort* lub
sortowanie przez "wyrównanie kawałków makaronu") to **fizyczny / analogowy**
algorytm sortowania, niezwykle prosty do zrozumienia, ale niemożliwy do
efektywnego zaimplementowania na klasycznym komputerze cyfrowym.

Algorytm:

1. Dla każdej liczby `x` w zbiorze, weź kawałek spaghetti (makaronu) o
   długości proporcjonalnej do `x` i przytnij go do tej długości.
2. Trzymaj wszystkie kawałki makaronu w pęczku, "stojąc" wertykalnie na
   stole (jak ołówki w kubku) — wyrównaj je tak, aby ich dolne końce
   dotykały stołu (działanie grawitacji).
3. Połóż rękę płasko nad pęczkiem i opuszczaj ją w dół — najpierw "złapiesz"
   najdłuższy kawałek (czyli największą liczbę).
4. Wyjmuj kawałki jeden po drugim, zaczynając od najdłuższego (lub
   najkrótszego, w zależności od kierunku) — otrzymując sekwencję
   posortowaną.

## Złożoność

- **Czas (fizyczny):** O(n) — przygotowanie kawałków zajmuje czas
  proporcjonalny do liczby elementów, a "wyciąganie" kolejnych elementów
  odbywa się w czasie stałym dzięki analogowej naturze problemu (wszystkie
  długości są "porównywane" jednocześnie przez grawitację i geometrię).
- **Czas (symulacja cyfrowa):** Tak naprawdę odpowiada to sortowaniu poprzez
  porównania O(n log n) lub, jeśli długości są ograniczone, sortowaniu
  kubełkowemu O(n + k).
- **Wymagania:** Potrzebuje **fizycznego nośnika** (makaron, druty, światło) —
  nie jest to algorytm "programistyczny" w klasycznym sensie.

## Pseudo-implementacja (symulacja)

```python
def spaghetti_sort(arr):
    # symulacja: każda wartość = "długość kawałka makaronu"
    # "wyrównanie do stołu" + "wyciąganie od najdłuższego"
    return sorted(arr, reverse=True)
```

(Rzeczywista implementacja w świecie fizycznym nie wymaga porównań — to
właśnie czyni ten algorytm "dziwnym": działa szybko fizycznie, ale jego
*symulacja cyfrowa* sprowadza się do banalnego `sorted()`.)

## Ciekawostki

- Spaghetti Sort jest często przywoływany w dyskusjach o **modelach obliczeń
  analogowych** — pyta: "co, jeśli nasz model obliczeń nie jest cyfrowy, a
  fizyczny?" Pokazuje, że granice złożoności obliczeniowej zależą od
  przyjętego modelu maszyny.
- Algorytm pojawia się w pracach popularnonaukowych i na forach (np. Stack
  Exchange) jako "myślowy eksperyment" pokazujący różnicę między teorią
  obliczeń a fizyczną realizacją.

## Źródła

- [Wikipedia (EN): Spaghetti sort](https://en.wikipedia.org/wiki/Spaghetti_sort)
- [Computer Science Stack Exchange: dyskusje o analogowych algorytmach sortowania](https://cs.stackexchange.com/questions/tagged/sorting)
