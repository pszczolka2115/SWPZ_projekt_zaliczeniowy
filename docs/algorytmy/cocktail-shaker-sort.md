# Cocktail Shaker Sort

## Opis

Cocktail Shaker Sort (znany też jako *Bidirectional Bubble Sort* lub
*Shaker Sort*) to wariant Bubble Sort, który — jak nazwa wskazuje —
"przelewa się" w obie strony, jak napój w shakerze barmana.

Algorytm:

1. Przejdź tablicę **od lewej do prawej**, zamieniając miejscami sąsiednie
   elementy, jeśli są w złej kolejności (jak w Bubble Sort) — "wypychając"
   największy element na koniec.
2. Przejdź tablicę **od prawej do lewej**, robiąc to samo — "wypychając"
   najmniejszy element na początek.
3. Zmniejsz zakres przeszukiwania z obu stron (granice już "ustawionych"
   elementów) i powtarzaj, aż żadna zamiana nie będzie potrzebna.

## Złożoność

- **Czas (najgorszy/przeciętny):** O(n²) — tak samo jak Bubble Sort.
- **Czas (najlepszy):** O(n) dla danych już posortowanych.
- **Pamięć:** O(1).
- **Zaleta względem Bubble Sort:** lepiej radzi sobie z tzw. "żółwiami"
  (małymi elementami znajdującymi się blisko końca tablicy), które w
  klasycznym Bubble Sort przesuwają się tylko o jedną pozycję na iterację.

## Przykład w Pythonie

```python
def cocktail_shaker_sort(arr):
    n = len(arr)
    start, end = 0, n - 1
    swapped = True
    while swapped:
        swapped = False
        for i in range(start, end):
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                swapped = True
        if not swapped:
            break
        end -= 1
        swapped = False
        for i in range(end - 1, start - 1, -1):
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                swapped = True
        start += 1
    return arr
```

## Ciekawostki

- Nazwa "cocktail" odnosi się do ruchu shakera barmana — "w jedną i drugą
  stronę". Algorytm jest popularnym przykładem "ulepszenia" prostego
  algorytmu poprzez zmianę kierunku przeszukiwania.
- Mimo że nadal ma złożoność O(n²), Cocktail Shaker Sort jest **stabilny** i
  bywa stosowany dydaktycznie jako "krok pomiędzy" Bubble Sort a bardziej
  zaawansowanymi technikami.

## Źródła

- [Wikipedia (EN): Cocktail shaker sort](https://en.wikipedia.org/wiki/Cocktail_shaker_sort)
