# Teoria — podstawy sortowania

## Co to jest algorytm sortowania?

Algorytm sortowania to procedura, która przyjmuje na wejściu kolekcję elementów
(np. listę liczb) i zwraca tę kolekcję uporządkowaną według określonego kryterium
(np. rosnąco lub malejąco).

## Jak oceniamy algorytmy sortowania?

### Złożoność czasowa

Najczęściej wyrażana w notacji **wielkiego O**, opisuje, jak czas działania
algorytmu rośnie w zależności od rozmiaru danych wejściowych `n`. Typowe klasy:

- `O(n log n)` — algorytmy "dobre" (MergeSort, HeapSort, QuickSort śr.)
- `O(n²)` — algorytmy "wolniejsze" (Bubble Sort, Insertion Sort)
- `O(n!)`, `O(2ⁿ)` lub gorzej — algorytmy "absurdalne" (Bogosort i podobne)

### Złożoność pamięciowa

Określa, ile dodatkowej pamięci potrzebuje algorytm — np. czy sortuje
"w miejscu" (`in-place`), czy wymaga dodatkowych struktur danych.

### Stabilność

Algorytm jest **stabilny**, jeśli zachowuje względną kolejność elementów
o równych wartościach.

### Porównawcze vs nieporównawcze

- **Algorytmy porównawcze** porządkują elementy poprzez porównania par
  (`a < b?`). Teoretyczna dolna granica złożoności dla tej klasy to `O(n log n)`.
- **Algorytmy nieporównawcze** (np. Bead Sort, Pigeonhole Sort) wykorzystują
  inne właściwości danych (np. zakres wartości) i mogą być szybsze w
  szczególnych przypadkach, ale często mają większe wymagania pamięciowe.

## Dlaczego "dziwne" algorytmy są warte uwagi?

Algorytmy takie jak Bogosort czy Stooge Sort nie mają zastosowania praktycznego
— ich złożoność jest katastrofalna. Mają jednak wartość:

- **edukacyjną** — pokazują "dolną granicę" tego, jak źle można podejść do
  problemu, co kontrastowo uczy doceniać dobre algorytmy,
- **rozrywkową** — są popularne w społecznościach programistycznych jako żarty,
- **historyczną/koncepcyjną** — niektóre (np. Bead Sort) inspirowane są
  zjawiskami fizycznymi i pokazują alternatywne modele obliczeń.

## Klasyfikacja algorytmów z tej strony

| Algorytm | Typ | Złożoność czasowa (śr.) |
|----------|-----|--------------------------|
| Bogosort | losowy, porównawczy | O((n+1)!) |
| Stooge Sort | rekurencyjny, porównawczy | O(n^2.71) |
| Slowsort | rekurencyjny ("multiply and surrender") | O(n^(log n)) |
| Gnome Sort | iteracyjny, porównawczy | O(n²) |
| Pancake Sort | iteracyjny, oparty na odwróceniach | O(n²) |
| Sleep Sort | współbieżny, czasowy | zależny od wartości |
| Bead Sort | nieporównawczy, fizyczny model | O(n) / O(√n) w sprzęcie |
| ICan'tBelieveItCanSort | iteracyjny, "głupi" insertion sort | O(n²) |
| Patience Sort | oparty na strukturze stosów | O(n log n) |
| Spaghetti Sort | analogowy / fizyczny | O(n) fizycznie |
| Odd-Even Transposition Sort | równoległy | O(n) na n procesorach |
| Cocktail Shaker Sort | dwukierunkowy bubble sort | O(n²) |
| Quantum Bogosort | teoretyczny / żartobliwy | O(n) (teoretycznie) |
| Random Sort (Shuffle Sort) | losowy | nieograniczone |

Każdy z tych algorytmów został opisany w osobnym artykule w sekcji
**Algorytmy**, wraz ze źródłami.

## Źródła ogólne

- [Wikipedia (PL): Algorytm sortujący](https://pl.wikipedia.org/wiki/Algorytm_sortuj%C4%85cy)
- [Wikipedia (EN): Sorting algorithm](https://en.wikipedia.org/wiki/Sorting_algorithm)
- [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)
