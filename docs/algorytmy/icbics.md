# I Can't Believe It Can Sort

## Opis

"I Can't Believe It Can Sort" (ICan'tBelieveItCanSort) to algorytm, którego
nazwa odzwierciedla reakcję, jaką wywołuje u osób analizujących jego kod —
ponieważ wygląda na **błędną** implementację, a jednak poprawnie sortuje
tablicę.

Algorytm wykorzystuje **dwie zagnieżdżone pętle for**, ale w nietypowy sposób:
zamiast porównywać elementy ze sobą "z sensem" (jak w Selection Sort czy
Bubble Sort), porównuje *każdy* element z *każdym* i zamienia je miejscami,
jeśli są w złej kolejności — niezależnie od tego, czy `i < j` czy `i > j`.

```text
for i from 0 to n-1:
    for j from 0 to n-1:
        if A[i] < A[j] and i > j:
            swap(A[i], A[j])
        if A[i] > A[j] and i < j:
            swap(A[i], A[j])
```

Mimo że wygląda to jak "podwójny Bubble Sort robiący dwa razy za dużo pracy",
algorytm faktycznie poprawnie sortuje tablicę — stąd nazwa.

## Złożoność

- **Czas:** O(n²) — tak samo jak Bubble Sort czy Selection Sort, mimo że
  wykonuje znacznie więcej porównań i zamian niż konieczne.
- **Pamięć:** O(1) — sortowanie w miejscu.
- **Stabilność:** Algorytm **nie jest stabilny**.

## Przykład w Pythonie

```python
def icbics(arr):
    n = len(arr)
    for i in range(n):
        for j in range(n):
            if arr[i] < arr[j] and i > j:
                arr[i], arr[j] = arr[j], arr[i]
            if arr[i] > arr[j] and i < j:
                arr[i], arr[j] = arr[j], arr[i]
    return arr
```

## Ciekawostki

- Algorytm został opisany przez Stanforda Felixa "stanford-cs161" / pojawił się
  w dyskusjach społeczności programistycznych jako przykład tego, że "działa"
  nie znaczy "działa dobrze lub elegancko" — wiele osób przy pierwszym
  spojrzeniu zakłada, że kod ma błąd logiczny.
- Jest często wykorzystywany jako "zagadka" na rozmowach kwalifikacyjnych lub
  zajęciach — "udowodnij, że ten kod faktycznie sortuje".

## Źródła

- [Wikipedia (EN): I Can't Believe It Can Sort](https://en.wikipedia.org/wiki/I_Can%27t_Believe_It_Can_Sort)
