# Pancake Sort

## Opis

Pancake Sort to algorytm modelujący problem sortowania jako układanie stosu
naleśników o różnych rozmiarach — przy czym jedyną dostępną operacją jest
**"łopatka" (flip)**: wsunięcie łopatki pod k-ty naleśnik od dołu i odwrócenie
całego stosu nad nią.

Algorytm:

1. Znajdź największy nieposortowany element w aktualnym zakresie.
2. Odwróć podtablicę od początku do tego elementu, tak aby trafił on na
   szczyt (na początek aktualnego zakresu).
3. Odwróć cały aktualny zakres, przenosząc ten element na właściwą (ostatnią)
   pozycję w zakresie.
4. Zmniejsz zakres o 1 i powtórz, aż zakres będzie miał 1 element.

## Złożoność

- **Czas:** O(n²) — w każdej z n iteracji wykonujemy operację flip kosztującą
  O(n).
- **Liczba flipów:** Można wykazać, że wystarczy co najwyżej `2n - 3` flipów
  (dla n ≥ 2), co jest istotne w analizie tzw. **liczb naleśnikowych**
  (pancake numbers).
- **Pamięć:** O(1) — sortowanie w miejscu.

## Przykład w Pythonie

```python
def flip(arr, k):
    arr[:k+1] = arr[:k+1][::-1]

def pancake_sort(arr):
    n = len(arr)
    for size in range(n, 1, -1):
        max_idx = arr.index(max(arr[:size]))
        if max_idx != size - 1:
            flip(arr, max_idx)
            flip(arr, size - 1)
    return arr
```

## Ciekawostki

- Problem "Pancake problem" (znajdź minimalną liczbę flipów potrzebną do
  posortowania stosu naleśników w najgorszym przypadku) został spopularyzowany
  przez Jacoba E. Goodmana w 1975 roku.
- Bill Gates, jeszcze jako student, współautorował artykuł naukowy (1979,
  wraz z Christosem Papadimitriou) podający górne ograniczenie dla wariantu
  tego problemu, w którym naleśniki mogą być "przypalone" tylko z jednej
  strony (tzw. *burnt pancake problem*).

## Źródła

- [Wikipedia (EN): Pancake sorting](https://en.wikipedia.org/wiki/Pancake_sorting)
- [Wikipedia (EN): Pancake graph (kontekst matematyczny)](https://en.wikipedia.org/wiki/Pancake_graph)
