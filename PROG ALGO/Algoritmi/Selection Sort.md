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