# Quantum Bogosort

## Opis

Quantum Bogosort (Quantum Bogosortowanie) to **żartobliwy algorytm
teoretyczny**, łączący Bogosort z koncepcjami z mechaniki kwantowej —
konkretnie z interpretacją wieloświatową (*many-worlds interpretation*).

Algorytm:

1. Wygeneruj losową permutację tablicy, wykorzystując **kwantowy generator
   losowości** — który (zgodnie z interpretacją wieloświatową) tworzy
   superpozycję, w której każda możliwa permutacja "istnieje" w innym
   wszechświecie równoległym.
2. Sprawdź, czy tablica jest posortowana.
3. **Jeśli nie jest posortowana — zniszcz wszechświat** (np. poprzez
   detonację bomby podłączonej do detektora kwantowego).
4. Jeśli tablica jest posortowana, algorytm "się powiódł" — a ponieważ
   wszystkie wszechświaty, w których wynik był błędny, zostały zniszczone,
   obserwator zawsze znajdzie się w tym jedynym wszechświecie, w którym
   tablica jest posortowana.

## Złożoność

- **Czas (subiektywny, z punktu widzenia "ocalałego" obserwatora):** O(n) —
  algorytm "kończy się" w jednym kroku!
- **Czas (obiektywny / koszt):** Wymaga zniszczenia (n! - 1) / n! wszechświatów
  — co jest oczywistym żartem, a nie realnym kosztem obliczeniowym w
  jakimkolwiek mierzalnym sensie.
- **Wymagania:** Działający komputer kwantowy + akceptacja interpretacji
  wieloświatowej mechaniki kwantowej + bardzo specyficzne podejście do
  etyki.

## Pseudokod (żartobliwy)

```text
function quantum_bogosort(array):
    permutation = quantum_random_permutation(array)
    if not is_sorted(permutation):
        destroy_universe()
    return permutation
```

## Ciekawostki

- Quantum Bogosort jest czystym **żartem informatycznym/filozoficznym** —
  nigdy nie był (i nie może być) zaimplementowany w praktyce.
- Algorytm jest często przywoływany jako ilustracja absurdalnych konsekwencji
  niektórych interpretacji mechaniki kwantowej, gdy zastosuje się je
  "naiwnie" do problemów obliczeniowych.
- Pojawia się w artykule Wikipedii o Bogosort jako jeden z "wariantów"
  Bogosort, obok Bozosort i innych.

## Źródła

- [Wikipedia (EN): Bogosort — sekcja "Related algorithms" (Quantum bogosort)](https://en.wikipedia.org/wiki/Bogosort)
