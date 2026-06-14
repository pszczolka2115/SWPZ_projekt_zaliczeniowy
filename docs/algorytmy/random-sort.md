# Random Sort (Shuffle Sort)

## Opis

Random Sort, czasem nazywany *Shuffle Sort* lub *Dance Sort*, to rodzina
algorytmów opierających się na **losowym przestawianiu elementów** w
nadziei, że w końcu trafi się porządek właściwy — różniąca się od Bogosortu
głównie metodą generowania kolejnej permutacji oraz sposobem sprawdzania
postępu.

Najprostsza wersja:

1. Wybierz dwa losowe indeksy `i` i `j`.
2. Zamień miejscami `A[i]` i `A[j]`.
3. Sprawdź, czy tablica jest posortowana.
4. Jeśli nie — wróć do punktu 1.

Różnica względem Bogosortu: tutaj **nie generujemy całej nowej permutacji**,
a jedynie wykonujemy jedną losową zamianę — co teoretycznie może (ale nie
musi) przybliżać nas do rozwiązania, jak w "błądzeniu losowym" (random walk).

## Złożoność

- **Czas:** Nieograniczony / losowy — w najgorszym przypadku algorytm może
  działać w nieskończoność (tablica może "błąkać się" losowo bez końca).
  W praktyce oczekiwany czas jest gorszy niż dla algorytmów klasycznych, ale
  zazwyczaj lepszy niż "czysty" Bogosort (ponieważ losowe zamiany czasem
  "utrwalają" częściowy porządek).
- **Pamięć:** O(1).
- **Determinizm:** Brak — wynik (czas działania) zależy od generatora liczb
  losowych.

## Przykład w Pythonie

```python
import random

def is_sorted(arr):
    return all(arr[i] <= arr[i+1] for i in range(len(arr)-1))

def random_sort(arr):
    n = len(arr)
    while not is_sorted(arr):
        i, j = random.randrange(n), random.randrange(n)
        arr[i], arr[j] = arr[j], arr[i]
    return arr
```

## Ciekawostki

- Random Sort/Shuffle Sort bywa wykorzystywany jako **przykład błądzenia
  losowego (random walk)** w analizie algorytmów probabilistycznych — pytanie
  "ile losowych zamian potrzeba, aby z prawdopodobieństwem 99% otrzymać
  posortowaną tablicę?" jest nietrywialnym zagadnieniem matematycznym.
- Czasem prezentowany jako "naturalna ewolucja" Bogosortu — pokazuje, że
  nawet niewielka zmiana strategii (cała permutacja vs jedna zamiana) może
  diametralnie zmienić zachowanie algorytmu (choć wciąż katastrofalnie
  nieefektywnego dla większych n).

## Źródła

- [Wikipedia (EN): Bogosort — kontekst wariantów losowych](https://en.wikipedia.org/wiki/Bogosort)
- [Wikipedia (EN): Random walk (kontekst matematyczny)](https://en.wikipedia.org/wiki/Random_walk)
