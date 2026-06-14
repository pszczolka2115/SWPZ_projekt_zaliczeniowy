# Gnome Sort

## Opis

Gnome Sort (zwany też *Stupid Sort*) to algorytm zainspirowany sposobem,
w jaki — według autora — ogrodowy gnom mógłby sortować doniczki: patrzy na
bieżącą i poprzednią doniczkę; jeśli są w dobrej kolejności, robi krok do
przodu; jeśli nie — zamienia je miejscami i robi krok do tyłu.

Algorytm:

1. Ustaw wskaźnik `pos = 0`.
2. Jeśli `pos == 0` lub `A[pos] >= A[pos-1]`, zwiększ `pos` o 1.
3. W przeciwnym razie zamień `A[pos]` i `A[pos-1]` miejscami i zmniejsz `pos`
   o 1.
4. Powtarzaj, aż `pos` osiągnie koniec tablicy.

## Złożoność

- **Czas:** O(n²) w najgorszym i przeciętnym przypadku, O(n) dla danych już
  posortowanych.
- **Pamięć:** O(1) — sortowanie w miejscu.

Pod względem złożoności Gnome Sort jest podobny do Insertion Sort, ale jego
implementacja jest prostsza — nie wymaga zagnieżdżonej pętli, tylko jednego
wskaźnika i instrukcji warunkowej.

## Przykład w Pythonie

```python
def gnome_sort(arr):
    pos = 0
    n = len(arr)
    while pos < n:
        if pos == 0 or arr[pos] >= arr[pos - 1]:
            pos += 1
        else:
            arr[pos], arr[pos - 1] = arr[pos - 1], arr[pos]
            pos -= 1
    return arr
```

## Ciekawostki

- Algorytm został opisany (pod nazwą "Stupid sort") przez Dicka Grune'a,
  a nazwę "Gnome Sort" spopularyzował Hamid Sarbazi-Azad w 2000 roku,
  porównując działanie algorytmu do gnoma porządkującego doniczki z kwiatami.
- Mimo "głupiej" nazwy, algorytm jest poprawny i czasem używany jako proste
  ćwiczenie programistyczne dla początkujących.

## Źródła

- [Wikipedia (EN): Gnome sort](https://en.wikipedia.org/wiki/Gnome_sort)
- [GeeksforGeeks: Gnome Sort](https://www.geeksforgeeks.org/gnome-sort-a-stupid-one/)
