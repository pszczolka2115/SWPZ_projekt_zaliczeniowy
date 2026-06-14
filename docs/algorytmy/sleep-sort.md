# Sleep Sort

## Opis

Sleep Sort to algorytm, który stał się internetowym memem programistycznym po
opublikowaniu w 2011 roku na anonimowym forum (4chan). Jego "elegancja"
polega na tym, że **nie wykonuje żadnych porównań** — wykorzystuje natomiast
mechanizm "uśpienia" wątku/procesu na czas proporcjonalny do wartości elementu.

Algorytm:

1. Dla każdego elementu `x` w tablicy wejściowej, uruchom nowy wątek/proces.
2. Każdy wątek "śpi" przez czas proporcjonalny do `x` (np. `x` sekund lub
   milisekund).
3. Po przebudzeniu, wątek wypisuje (lub dodaje do wyniku) swoją wartość `x`.
4. Elementy "wypisują się" w kolejności rosnącej — ponieważ mniejsze wartości
   "śpią" krócej.

## Złożoność

- **Czas:** W teorii O(max(input) + n) — zależy od **wartości** elementów, nie
  od ich liczby, co jest sprzeczne z klasyczną analizą złożoności
  porównawczych algorytmów sortowania.
- **Pamięć:** O(n) — jeden wątek/proces na element.
- **Ograniczenia:** Algorytm nie działa dla liczb ujemnych lub zerowych bez
  modyfikacji, jest niedeterministyczny (zależy od planisty systemu
  operacyjnego) i praktycznie nieskalowalny (tysiące wątków dla dużych
  danych).

## Przykład w Pythonie

```python
import threading
import time

def sleep_sort(arr):
    result = []
    def worker(x):
        time.sleep(x / 100)  # skalowanie, by uniknąć zbyt długiego czekania
        result.append(x)

    threads = [threading.Thread(target=worker, args=(x,)) for x in arr]
    for t in threads:
        t.start()
    for t in threads:
        t.join()
    return result
```

## Ciekawostki

- Sleep Sort jest klasycznym przykładem algorytmu, który "działa", ale
  całkowicie ignoruje to, co normalnie rozumiemy jako "sortowanie" — nie
  porównuje elementów, lecz wykorzystuje zegar systemowy jako "strukturę
  danych".
- Bywa wskazywany jako żartobliwy przykład w dyskusjach o złożoności
  obliczeniowej — pokazuje, że "czas rzeczywisty" nie jest tym samym, co
  liczba operacji.

## Źródła

- [Rosetta Code: Sorting algorithms/Sleep sort](https://rosettacode.org/wiki/Sorting_algorithms/Sleep_sort)
- [Know Your Meme: Sleep Sort (kontekst popularności)](https://knowyourmeme.com/memes/sleep-sort)
