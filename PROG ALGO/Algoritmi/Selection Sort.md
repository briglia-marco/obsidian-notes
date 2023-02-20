# Pseudocodice

```js
function selectionSort(A) {
  for (let i = 0; i < A.length - 1; i++) {
    let minIndex = i;
    for (let j = i + 1; j < A.length; j++) {
      if (A[j] < A[minIndex]) {
        minIndex = j;
      }
    }
    [A[i], A[minIndex]] = [A[minIndex], A[i]];
  }
}

```

# Pro e Contro

Vantaggi:

-   È semplice da implementare e capire, poiché utilizza solo due cicli.
-   È stabile, ovvero mantiene l'ordine relativo degli elementi uguali.
-   Utilizza poco spazio extra, poiché non richiede [[array]] o strutture dati aggiuntive.

Svantaggi:

-   Non è molto efficiente per grandi set di dati.
-   Non è un algoritmo adatto per l'elaborazione in tempo reale poiché la sua complessità è elevata
-   In alcune situazioni potrebbe essere più lento dell'algoritmo di ordinamento per inserimento.

# Complessità

La complessità è sempre O(n^2) ad ogni caso

# Dimostrazione di Correttezza 

Per dimostrare la correttezza dell'insertion sort, dobbiamo dimostrare che l'algoritmo termina correttamente e che alla fine restituisce un [[array]] ordinato. Inoltre, dobbiamo dimostrare che l'insertion sort mantiene la proprietà dell'invariante di ciclo, ovvero che ogni iterazione del ciclo principale dell'algoritmo preserva l'ordinamento dell'array.

Supponiamo che l'array da ordinare sia A[1...n]. L'insertion sort itera attraverso gli elementi da A[2] ad A[n], e in ogni iterazione inserisce l'elemento corrente nell'array ordinato A[1...j-1]. Inizialmente, A[1] forma una porzione ordinata di lunghezza 1.

All'inizio di ogni iterazione i del ciclo principale, la porzione di array A[1...i-1] è ordinata. L'elemento corrente A[i] viene inserito nella porzione ordinata, spostando gli elementi maggiori di A[i] di una posizione verso destra, finché non viene trovata la posizione corretta per inserire A[i]. Una volta che A[i] viene inserito nella posizione corretta, la porzione ordinata diventa A[1...i].

L'invariante di ciclo è quindi che, all'inizio di ogni iterazione i del ciclo principale, la porzione di array A[1...i-1] è ordinata. Inoltre, ogni volta che un nuovo elemento A[i] viene inserito nella porzione ordinata, la porzione ordinata viene estesa di un elemento.

Alla fine dell'ultimo ciclo, l'intero array A[1...n] è ordinato. Infatti, l'ultimo elemento A[n] viene inserito nella porzione ordinata A[1...n-1], e la porzione ordinata diventa l'intero array A[1...n].