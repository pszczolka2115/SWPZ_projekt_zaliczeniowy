# Odd-Even Transposition Sort

## Opis

Odd-Even Transposition Sort (sortowanie przez transpozycje nieparzyste-parzyste)
to algorytm zaprojektowany pod kątem **architektur równoległych** — np.
sieci procesorów połączonych liniowo. Jest "dziwny" w kontekście tej strony,
bo na pierwszy rzut oka przypomina prosty Bubble Sort, ale jego struktura
ma sens głównie przy pełnej równoległości.

Algorytm działa w cyklach:

1. **Faza nieparzysta:** porównaj i ewentualnie zamień parę elementów na
   pozycjach (1,2), (3,4), (5,6), ...
2. **Faza parzysta:** porównaj i ewentualnie zamień parę elementów na
   pozycjach (0,1), (2,3), (4,5), ...
3. Powtarzaj fazy na przemian, aż żadna zamiana nie będzie potrzebna (lub po
   n iteracjach).

## Złożoność

- **Czas (sekwencyjnie):** O(n²) — identycznie jak Bubble Sort.
- **Czas (na n procesorach równoległych):** O(n) — każda faza wykonuje się
  w czasie O(1), a potrzeba O(n) faz.
- **Pamięć:** O(1) dodatkowej pamięci na element (każdy procesor przechowuje
  jeden element).

## Przykład w Pythonie (wersja sekwencyjna)

```python
def odd_even_sort(arr):
    n = len(arr)
    sorted_ = False
    while not sorted_:
        sorted_ = True
        for i in range(1, n - 1, 2):  # faza nieparzysta
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                sorted_ = False
        for i in range(0, n - 1, 2):  # faza parzysta
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                sorted_ = False
    return arr
```

## Ciekawostki

- Algorytm jest klasycznym przykładem w kursach **programowania
  równoległego/sieci sortujących** (sorting networks) — pokazuje, jak
  "zwykły" algorytm O(n²) może stać się O(n), jeśli mamy do dyspozycji
  odpowiednią liczbę jednostek przetwarzających.
- Jest "dziwny" na tej stronie nie dlatego, że jest absurdalny, ale dlatego,
  że jego efektywność **zależy całkowicie od modelu sprzętowego**, a nie od
  samego algorytmu.

## Źródła

- [Wikipedia (EN): Odd–even sort](https://en.wikipedia.org/wiki/Odd%E2%80%93even_sort)
