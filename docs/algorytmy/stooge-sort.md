# Stooge Sort

## Opis

Stooge Sort to rekurencyjny algorytm sortowania, którego nazwa wzięta jest od
komediowego trio *The Three Stooges* — odzwierciedlając "niezgrabność" i
nadmiarowość jego działania.

Algorytm działa na tablicy `A[i..j]` w następujący sposób:

1. Jeśli `A[i] > A[j]`, zamień je miejscami.
2. Jeśli w przedziale `[i, j]` jest więcej niż 2 elementy:
      - posortuj rekurencyjnie pierwsze 2/3 elementów,
      - posortuj rekurencyjnie ostatnie 2/3 elementów,
      - jeszcze raz posortuj rekurencyjnie pierwsze 2/3 elementów.

Ten "potrójny" podział na zazębiające się 2/3 fragmenty powoduje ogromną
nadmiarowość obliczeń.

## Złożoność

- **Czas:** O(n^(log 3 / log 1.5)) ≈ O(n^2.7095)
- **Pamięć:** O(log n) (na stos wywołań rekurencyjnych)

Mimo że jest to algorytm porównawczy działający "w miejscu", jego złożoność
jest znacznie gorsza niż klasyczny Bubble Sort (O(n²)).

## Przykład w Pythonie

```python
def stooge_sort(arr, i=0, j=None):
    if j is None:
        j = len(arr) - 1
    if arr[i] > arr[j]:
        arr[i], arr[j] = arr[j], arr[i]
    if j - i + 1 > 2:
        third = (j - i + 1) // 3
        stooge_sort(arr, i, j - third)
        stooge_sort(arr, i + third, j)
        stooge_sort(arr, i, j - third)
    return arr
```

## Ciekawostki

- Stooge Sort jest często wykorzystywany na zajęciach z analizy algorytmów
  jako przykład rekurencji, która jest poprawna, ale wyjątkowo nieefektywna.
- Mimo gorszej złożoności niż Bubble Sort, dla bardzo małych tablic różnica
  praktyczna bywa niezauważalna.

## Źródła

- [Wikipedia (EN): Stooge sort](https://en.wikipedia.org/wiki/Stooge_sort)
- [GeeksforGeeks: Stooge Sort](https://www.geeksforgeeks.org/stooge-sort/)
