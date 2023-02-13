# Pseudocodice

```js
function mergesort(A, start, end) {
  if (start < end) {
    let mid = Math.floor((start + end) / 2);
    mergesort(A, start, mid);
    mergesort(A, mid + 1, end);
    merge(A, start, mid, end);
  }
}

function merge(A, start, mid, end) {
  let leftLength = mid - start + 1;
  let rightLength = end - mid;
  let left = [];
  let right = [];

  for (let i = 0; i < leftLength; i++) {
    left[i] = A[start + i];
  }
  for (let j = 0; j < rightLength; j++) {
    right[j] = A[mid + 1 + j];
  }

  let i = 0;
  let j = 0;
  let k = start;

  while (i < leftLength && j < rightLength) {
    if (left[i] <= right[j]) {
      A[k] = left[i];
      i++;
    } else {
      A[k] = right[j];
      j++;
    }
    k++;
  }

  while (i < leftLength) {
    A[k] = left[i];
    i++;
    k++;
  }

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

