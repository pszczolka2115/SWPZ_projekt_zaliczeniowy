# Bogosort

## Opis

Bogosort (znany też jako *permutation sort*, *stupid sort* lub *random sort*)
to być może najsłynniejszy "żartobliwy" algorytm sortowania. Jego zasada
działania jest brutalnie prosta:

1. Sprawdź, czy lista jest już posortowana.
2. Jeśli nie — wylosuj nową, losową permutację elementów.
3. Wróć do punktu 1.

Algorytm działa więc na zasadzie "losuj, aż się uda" (czasem nazywanej
*generate and test*).

## Złożoność

- **Czas (przeciętny przypadek):** O((n+1)!) — dla każdej permutacji tablicy
  o n elementach mamy 1/n! szansy, że jest ona posortowana.
- **Czas (najgorszy przypadek):** nieograniczony — teoretycznie algorytm może
  nigdy się nie zakończyć.
- **Pamięć:** O(1) dodatkowej pamięci (poza samą tablicą).

Już dla n=10 oczekiwana liczba prób wynosi ponad 3 miliony, co praktycznie
dyskwalifikuje algorytm dla list większych niż kilka elementów.

## Przykład w Pythonie

```python
import random

def is_sorted(data):
    return all(data[i] <= data[i+1] for i in range(len(data)-1))

def bogosort(data):
    while not is_sorted(data):
        random.shuffle(data)
    return data
```

## Ciekawostki

- Bogosort jest często wykorzystywany jako "żart programistyczny" w kursach
  algorytmiki, aby zilustrować, jak źle może wyglądać algorytm losowy.
- Istnieją warianty, takie jak *Bozosort* (zamienia tylko dwa losowe elementy,
  jeśli lista nie jest posortowana) czy *Quantum Bogosort* (opisany w
  osobnym artykule).
- Nazwa pochodzi od angielskiego slangu "bogus", czyli "fałszywy, do niczego".

## Źródła

- [Inefficient sort algorithms (EN)[WebArchive]](https://web.archive.org/web/20131210012102/http://richardhartersworld.com/cri_d/cri/2001/badsort.html)
- [Sorting the Slow Way: An Analysis of Perversely Awful Randomized Sorting Algorithms](http://www.hermann-gruber.com/pdf/fun07-final.pdf)
