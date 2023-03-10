# Pseudocodice

```js
// funzione mergesort che prende come argomenti un array A, l'indice di inizio e l'indice di fine
function mergesort(A, start, end) {
  // condizione di uscita della ricorsione, se start è maggiore o uguale a end l'array è già ordinato
  if (start < end) {
    // calcola l'indice medio dell'array
    let mid = Math.floor((start + end) / 2);
    // chiama ricorsivamente mergesort sulla metà sinistra dell'array
    mergesort(A, start, mid);
    // chiama ricorsivamente mergesort sulla metà destra dell'array
    mergesort(A, mid + 1, end);
    // fonde le due metà dell'array ordinato
    merge(A, start, mid, end);
  }
}

// funzione merge che prende come argomenti un array A, l'indice di inizio, l'indice medio e l'indice di fine
function merge(A, start, mid, end) {
  // calcola la lunghezza dell'array di sinistra e di destra
  let leftLength = mid - start + 1;
  let rightLength = end - mid;
  // crea due array vuoti per la metà sinistra e destra dell'array
  let left = [];
  let right = [];

  // copia gli elementi della metà sinistra dell'array in left
  for (let i = 0; i < leftLength; i++) {
    left[i] = A[start + i];
  }
  // copia gli elementi della metà destra dell'array in right
  for (let j = 0; j < rightLength; j++) {
    right[j] = A[mid + 1 + j];
  }

  // inizializza tre indici, uno per left, uno per right e uno per A
  let i = 0;
  let j = 0;
  let k = start;

  // finché ci sono elementi sia in left che in right
  while (i < leftLength && j < rightLength) {
    // confronta gli elementi in left e right
    if (left[i] <= right[j]) {
      // se l'elemento in left è minore o uguale all'elemento in right, lo copia in A e incrementa l'indice di left
      A[k] = left[i];
      i++;
    } else {
      // altrimenti copia l'elemento in right in A e incrementa l'indice di right
      A[k] = right[j];
      j++;
    }
    // incrementa l'indice di A
    k++;
  }

  // copia eventuali elementi rimanenti in left
  while (i < leftLength) {
    A[k] = left[i];
    i++;
    k++;
  }

  // copia eventuali elementi rimanenti in right
  while (j < rightLength) {
    A[k] = right[j];
    j++;
    k++;
  }
}
```

# Pro e Contro

Vantaggi:

-   È stabile, cioè non cambia l'ordine degli elementi uguali.    
-   Ha una complessità O(n * log n) in ogni caso, sia per il caso migliore, medio e peggiore.
-   È facilmente implementabile in modo ricorsivo.
-   Utile per insiemi di grandi dimensioni (>1M)

Svantaggi:

-   Richiede spazio extra per gli array temporanei utilizzati nella procedura di `merge`.    
-   Può essere più lento rispetto ad altri algoritmi di ordinamento come [[Quick Sort]] in alcuni casi particolari, come ad esempio quando l'input è già ordinato.
-   Non è adatto per ordinare grandi quantità di dati su dispositivi con limitati spazi di memoria.


# Complessità

-   Caso migliore: O(n * log n) - quando l'array è già ordinato, il merge sort effettua n-1 confronti per stabilire che l'array è ordinato e quindi non effettua alcuna operazione di merge. In questo caso, il numero di confronti è O(n) e il numero di operazioni di merge è O(log n).

-   Caso medio: O(n * log n) - quando gli elementi sono in un ordine casuale, il merge sort effettua n log n confronti e operazioni di merge.

-   Caso peggiore: O(n * log n) - quando l'array è ordinato in ordine inverso, il merge sort effettua n log n confronti e operazioni di merge.

| Caso Migliore | Caso Medio | Caso Peggiore |
| ------------- | ---------- | ------------- |
| O(nlogn)      | O(nlogn)   | O(nlogn)        |

# Dimostrazione di Correttezza

Per dimostrare la correttezza del merge sort, dobbiamo dimostrare che l'algoritmo termina correttamente e che alla fine restituisce un [[array]] ordinato. Inoltre, dobbiamo dimostrare che il merge sort mantiene la proprietà dell'invariante di ciclo, ovvero che ogni iterazione del ciclo principale dell'algoritmo preserva l'ordinamento dell'array.

Supponiamo che l'array da ordinare sia A[1...n]. Il merge sort divide ricorsivamente l'array in due parti, A[1...m] e A[m+1...n], dove m è l'indice di mezzo dell'array. Poi, ordina le due parti separatamente, applicando ricorsivamente il merge sort. Infine, unisce le due parti ordinate in un array ordinato.

L'invariante di ciclo è che, in ogni iterazione del ciclo principale dell'algoritmo, l'array A[1...i-1] è ordinato e contiene i primi i-1 elementi ordinati. Inoltre, l'array A[i...n] contiene gli elementi non ordinati rimanenti.

Durante l'operazione di unione, il merge sort combina due array ordinati A[1...m] e A[m+1...n] in un unico array ordinato. L'algoritmo confronta gli elementi di A[1...m] e A[m+1...n] in ordine e seleziona l'elemento più piccolo, aggiungendolo all'array ordinato. Questo procedimento continua finché tutti gli elementi di entrambe le parti non sono stati inseriti nell'array ordinato.

Alla fine dell'operazione di unione, l'array A[1...n] è ordinato. Infatti, l'operazione di unione ordina gli elementi di A[1...m] e A[m+1...n] in un array ordinato A[1...n]. Inoltre, la proprietà dell'invariante di ciclo viene preservata durante l'operazione di unione.

In ogni passaggio ricorsivo, l'array viene diviso in due parti e il merge sort viene applicato a ciascuna parte separatamente. L'invariante di ciclo viene mantenuta in ogni passaggio ricorsivo e alla fine l'intero array viene unito in un array ordinato.