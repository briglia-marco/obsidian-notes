# Pseudocodice

```js
function quicksort(A, inizio, fine) {
  //se ci sono ancora elementi da ordinare
  if (inizio < fine) {
    //scegliere un elemento pivot e suddividi l'array in due parti
    var pivotIndex = partition(A, inizio, fine);
    //ordina la parte sinistra dell'array
    quicksort(A, inizio, pivotIndex);
    //ordina la parte destra dell'array
    quicksort(A, pivotIndex + 1, fine);
  }
}

function partition(A, inizio, fine) {
  var pivot = A[fine];
  //indice utilizzato per scambiare gli elementi
  var i = inizio - 1;
  //iteriamo sull'array
  for (var j = inizio; j < fine; j++) {
    if (A[j] <= pivot) {
      i++;
      //scambia A[i] con A[j]
      var temp = A[i];
      A[i] = A[j];
      A[j] = temp;
    }
  }
  //alla fine scambiamo l'elemento pivot con quello alla posizione "i+1"
  var temp = A[i + 1];
  A[i + 1] = A[fine];
  A[fine] = temp;
  //questa è la posizione del pivot
  return i + 1;
}

```

# Pro e Contro

Vantaggi:

-   È un algoritmo veloce in generale, con una complessità di O(n * log(n)) nella media, e quindi è spesso utilizzato in molti sistemi di ordinamento di grandi quantità di dati.
-   Non ha bisogno di uno spazio extra per ordinare i dati, poiché utilizza la tecnica "divide et impera" per ordinare i dati in-place.
-   È un algoritmo stabile, ciò significa che mantiene l'ordine relativo degli elementi uguali.

Svantaggi:

-   Nel peggiore dei casi, quando l'algoritmo sceglie un elemento pivot non appropriato, la complessità può diventare O(n^2), rendendo l'algoritmo molto lento.
-   È un algoritmo meno efficiente rispetto ad altri algoritmi di ordinamento come MergeSort perché utilizza molte chiamate ricorsive, quindi può causare problemi di memoria se si stanno ordinando grandi quantità di dati.
-   Non è deterministico, quindi potrebbe non ordinare gli stessi dati nello stesso modo ogni volta.

# Complessità

-   Nel caso migliore, quando l'algoritmo sceglie sempre l'elemento mediano come pivot, la complessità è O(n * log(n)), dove n è il numero di elementi nell'array. In questo caso, l'algoritmo è molto efficiente e veloce.

-   Nel caso peggiore, quando l'algoritmo sceglie sempre l'elemento più grande o più piccolo come pivot, la complessità è O(n^2), dove n è il numero di elementi nell'array. In questo caso, l'algoritmo diventa molto lento e meno efficiente.

-   Nella media, la complessità è O(n * log(n)), rendendo l'algoritmo quicksort una scelta comune per l'ordinamento di grandi quantità di dati.

| Caso Migliore | Caso Medio | Caso Peggiore |
| ------------- | ---------- | ------------- |
| O(nlogn)      | O(nlogn)   | O(n^2)        |
