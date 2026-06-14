# Slowsort

## Opis

Slowsort to algorytm rekurencyjny zaprojektowany **specjalnie po to, aby być
maksymalnie wolny**, jednocześnie pozostając poprawny. Jest klasycznym
przykładem strategii nazywanej żartobliwie *"multiply and surrender"*
(parodia *"divide and conquer"* — "dziel i zwyciężaj" zamienione na
"rozmnóż i skapituluj").

Algorytm dla przedziału `[i, j]`:

1. Jeśli `i >= j`, zakończ (przedział jednoelementowy lub pusty jest
   "posortowany").
2. Wyznacz `m = (i + j) / 2`.
3. Posortuj rekurencyjnie `[i, m]`.
4. Posortuj rekurencyjnie `[m+1, j]`.
5. Jeśli `A[m] > A[j]`, zamień je miejscami.
6. Posortuj rekurencyjnie `[i, j-1]`.

Krok 6 powoduje, że algorytm wielokrotnie "przelicza" te same fragmenty
tablicy.

## Złożoność

- **Czas:** O(n^(log n)) — czyli **superpolinomialna**, ale wciąż lepsza niż
  wykładnicza.
- **Pamięć:** O(log n) na stos rekurencji.

To oznacza, że dla n=100 Slowsort jest astronomicznie wolniejszy niż np.
QuickSort, mimo że formalnie "kończy się" w czasie skończonym (w przeciwieństwie
do Bogosortu w najgorszym przypadku).

## Przykład w Pythonie

```python
def slowsort(arr, i=0, j=None):
    if j is None:
        j = len(arr) - 1
    if i >= j:
        return arr
    m = (i + j) // 2
    slowsort(arr, i, m)
    slowsort(arr, m + 1, j)
    if arr[m] > arr[j]:
        arr[m], arr[j] = arr[j], arr[m]
    slowsort(arr, i, j - 1)
    return arr
```

## Ciekawostki

- Slowsort został opisany w 1986 roku przez Andreia Broder i Jorge Stolfiego
  w pracy żartobliwie zatytułowanej "Pessimal Algorithms and Simplexity
  Analysis", wprowadzającej pojęcie *"simplexity"* — analogii do złożoności,
  ale dla algorytmów celowo nieefektywnych.
- Algorytm jest czasem prezentowany jako "antywzorzec" — przykład tego, jak
  *nie* projektować algorytmów rekurencyjnych.

## Źródła

- [Wikipedia (EN): Slowsort](https://en.wikipedia.org/wiki/Slowsort)
- [Wikipedia (EN): Pessimal Algorithms and Simplexity Analysis (kontekst)](https://en.wikipedia.org/wiki/Slowsort#History)
