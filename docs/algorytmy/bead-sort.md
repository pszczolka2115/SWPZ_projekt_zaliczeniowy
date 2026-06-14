# Bead Sort (Gravity Sort)

## Opis

Bead Sort, znany też jako **Gravity Sort**, to algorytm nieporównawczy
inspirowany fizycznym zjawiskiem grawitacji. Można go zobrazować jako
liczak (abakus): każda liczba reprezentowana jest jako rząd "korali"
nawleczonych na pionowe druty; gdy "puszczamy" je w dół (działanie
grawitacji), korale "opadają" i ułożenie ich w kolejnych rzędach od dołu
odpowiada posortowanym wartościom.

Algorytm (wersja koncepcyjna):

1. Reprezentuj każdą liczbę jako rząd korali (np. liczba 4 = 4 korale w
   rzędzie, pozycje 1-4 od lewej).
2. Ustaw korale na pionowych prętach (kolumny = wartości 1, 2, 3, ...).
3. "Pozwól" korlom opadać w dół pod wpływem grawitacji — każda kolumna
   zachowuje swoje korale, ale grawitacja powoduje, że "luki" są usuwane.
4. Po opadnięciu, odczytaj liczbę korali w każdym rzędzie od dołu — to
   posortowane wartości (od najmniejszej u góry do największej u dołu, lub
   odwrotnie, zależnie od konwencji).

## Złożoność

- **W implementacji sprzętowej (analogowej):** O(√n) lub nawet O(1) — bo
  "opadanie" odbywa się równolegle dla wszystkich korali dzięki fizyce.
- **W implementacji programowej (symulacja na komputerze cyfrowym):** O(n·S),
  gdzie S to suma wszystkich wartości — co w praktyce bywa znacznie gorsze
  niż klasyczne algorytmy O(n log n).
- **Ograniczenia:** Działa tylko dla **dodatnich liczb całkowitych**.
- **Pamięć:** O(n·max(arr)) w naiwnej implementacji (macierz korali).

## Przykład w Pythonie (symulacja)

```python
def bead_sort(arr):
    if not arr:
        return arr
    max_val = max(arr)
    # tworzymy "abakus" - macierz 0/1
    grid = [[1 if j < val else 0 for j in range(max_val)] for val in arr]
    # "opadanie" korali w każdej kolumnie
    for col in range(max_val):
        column_sum = sum(grid[row][col] for row in range(len(arr)))
        for row in range(len(arr)):
            grid[row][col] = 1 if row >= len(arr) - column_sum else 0
    # odczyt wyników (suma w każdym wierszu)
    return [sum(row) for row in grid]
```

## Ciekawostki

- Bead Sort to przykład algorytmu, w którym **fizyczna implementacja jest
  szybsza niż cyfrowa symulacja** — w realnym układzie korali na drutach,
  grawitacja działa na wszystkie korale "naraz", co odpowiada masowemu
  paralelizmowi niedostępnemu w typowym komputerze sekwencyjnym.
- Algorytm został opisany przez Josepha S. Arulanandhama, Cristiana S. Calude
  i Michaela J. Dinneena w 2002 roku jako przykład "naturalnego algorytmu"
  (natural computing).

## Źródła

- [Wikipedia (EN): Bead sort](https://en.wikipedia.org/wiki/Bead_sort)
- [GeeksforGeeks: Bead Sort (Gravity Sort)](https://www.geeksforgeeks.org/bead-sort-natural-sorting-algorithm/)
