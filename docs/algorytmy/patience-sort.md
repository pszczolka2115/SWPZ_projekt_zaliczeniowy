# Patience Sort

## Opis

Patience Sort to algorytm zainspirowany grą karcianą **pasjans** (stąd nazwa
"patience" — pacjans/cierpliwość). Wykorzystuje strukturę "stosów" (pile),
podobną do tej znanej z gry Klondike.

Algorytm:

1. Przechodź przez elementy tablicy wejściowej jeden po drugim.
2. Dla każdego elementu `x`, połóż go na **lewym możliwym stosie**, którego
   wierzch jest większy lub równy `x` (jeśli takiego stosu nie ma, utwórz
   nowy stos po prawej).
3. Po przetworzeniu wszystkich elementów, scal wszystkie stosy w jedną
   posortowaną sekwencję — wykorzystując operację podobną do scalania
   z Merge Sort (wybierając zawsze najmniejszy "wierzch" ze wszystkich
   stosów).

## Złożoność

- **Czas:** O(n log n) — co czyni go jednym z **niewielu "dziwnych"
  algorytmów na tej stronie, który jest praktycznie konkurencyjny** wobec
  klasycznych metod.
- **Pamięć:** O(n) — na stosy.
- **Dodatkowa właściwość:** Liczba utworzonych stosów odpowiada **długości
  najdłuższego rosnącego podciągu** (longest increasing subsequence) w danych
  wejściowych — co czyni Patience Sort użytecznym algorytmem do rozwiązania
  tego klasycznego problemu w O(n log n).

## Przykład w Pythonie

```python
import bisect

def patience_sort(arr):
    piles = []  # piles[i] = wierzchołek i-tego stosu
    for x in arr:
        idx = bisect.bisect_left(piles, x)
        if idx == len(piles):
            piles.append(x)
        else:
            piles[idx] = x
    # piles zawiera teraz posortowane "wierzchołki" - długość = LIS
    # (pełne sortowanie wymaga dodatkowego scalania ze śledzeniem elementów)
    return piles  # zwraca długość LIS i posortowane wierzchołki
```

## Ciekawostki

- Patience Sort wyróżnia się tym, że — w przeciwieństwie do większości
  algorytmów na tej stronie — **nie jest celowo nieefektywny**. Jego
  "dziwność" polega na nietypowej, karcianej metaforze i nieoczywistym
  zastosowaniu do problemu LIS.
- Algorytm bywa przypisywany informatykowi C.L. Mallowsowi (lata 60. XX
  wieku), który analizował go w kontekście kombinatoryki i prawdopodobieństwa.

## Źródła

- [Wikipedia (EN): Patience sorting](https://en.wikipedia.org/wiki/Patience_sorting)
