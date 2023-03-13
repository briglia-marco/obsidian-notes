# Pseudocodice
```js
function insertionSort(A) {
  // Itera sull'array partendo dall'indice 1
  for (let i = 1; i < A.length; i++) {
    // Crea una variabile j uguale a i
    let j = i;
    // Finché j è maggiore di 0 e l'elemento precedente è maggiore dell'elemento corrente
    while (j > 0 && A[j - 1] > A[j]) {
      // Scambia i due elementi utilizzando la destructuring assignment
      [A[j - 1], A[j]] = [A[j], A[j - 1]];
      // Decrementa j per continuare a confrontare l'elemento corrente con l'elemento precedente
      j--;
    }
  }
}

```

# Pro e Contro

Vantaggi:

-   E' semplice e facile da capire e implementare.
-   E' efficiente per dataset piccoli o già parzialmente ordinati.
-   E' un algoritmo stabile, ovvero mantiene l'ordine relativo degli elementi con lo stesso valore.

Svantaggi:
-   E' poco efficiente per dataset grandi
-   Non è adatto per l'elaborazione di grandi quantità di dati in tempo reale.

# Complessità

-   Caso migliore: O(n) - Questo si verifica quando l'array di input è già ordinato. In questo caso, il ciclo interno while non verrà eseguito affatto e l'algoritmo avrà bisogno di iterare attraverso l'array solo una volta.

-   Caso medio: O(n^2) - Questo si verifica quando l'array di input è ordinato in modo casuale. In questo caso, il ciclo interno while avrà bisogno di spostare alcuni elementi e l'algoritmo avrà bisogno di iterare attraverso l'array più volte.

-   Caso peggiore: O(n^2) - Questo si verifica quando l'array di input è ordinato in ordine inverso. In questo caso, il ciclo interno while avrà bisogno di spostare tutti gli elementi e l'algoritmo avrà bisogno di iterare attraverso l'array più volte.

| Caso Migliore | Caso Medio | Caso Peggiore |
| ------------- | ---------- | ------------- |
| O(n)          | O(n^2)     | O(n^2)        |

# Dimostrazione di correttezza

Per dimostrare la correttezza dell'insertion sort, dobbiamo dimostrare che l'algoritmo termina correttamente e che alla fine restituisce un array ordinato. Inoltre, dobbiamo dimostrare che l'insertion sort mantiene la proprietà dell'invariante di ciclo, ovvero che ogni iterazione del ciclo principale dell'algoritmo preserva l'ordinamento dell'array.

Supponiamo che l'array da ordinare sia A[1...n]. L'insertion sort itera attraverso gli elementi da A[2] ad A[n], e in ogni iterazione inserisce l'elemento corrente nell'array ordinato A[1...j-1]. Inizialmente, A[1] forma una porzione ordinata di lunghezza 1.

All'inizio di ogni iterazione i del ciclo principale, la porzione di array A[1...i-1] è ordinata. L'elemento corrente A[i] viene inserito nella porzione ordinata, spostando gli elementi maggiori di A[i] di una posizione verso destra, finché non viene trovata la posizione corretta per inserire A[i]. Una volta che A[i] viene inserito nella posizione corretta, la porzione ordinata diventa A[1...i].

L'invariante di ciclo è quindi che, all'inizio di ogni iterazione i del ciclo principale, la porzione di array A[1...i-1] è ordinata. Inoltre, ogni volta che un nuovo elemento A[i] viene inserito nella porzione ordinata, la porzione ordinata viene estesa di un elemento.

Alla fine dell'ultimo ciclo, l'intero array A[1...n] è ordinato. Infatti, l'ultimo elemento A[n] viene inserito nella porzione ordinata A[1...n-1], e la porzione ordinata diventa l'intero array A[1...n].
