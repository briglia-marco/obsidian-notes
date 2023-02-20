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

> Esiste una versione randomizzata del quicksort con la [[Selezione randomizzata]] che sceglie casualmente il pivot ad ogni ricorrenza del partition. 

# Pro e Contro

Vantaggi:

-   È un algoritmo veloce in generale, con una complessità di O(n * log(n)) nella media, e quindi è spesso utilizzato in molti sistemi di ordinamento di grandi quantità di dati.
-   Non ha bisogno di uno spazio extra per ordinare i dati, poiché utilizza la tecnica "[[Divide-et-impera|divide et impera]]" per ordinare i dati in-place.
-   È un algoritmo stabile, ciò significa che mantiene l'ordine relativo degli elementi uguali.

Svantaggi:

-   Nel peggiore dei casi, quando l'algoritmo sceglie un elemento pivot non appropriato, la complessità può diventare O(n^2), rendendo l'algoritmo molto lento.
-   È un algoritmo meno efficiente rispetto ad altri algoritmi di ordinamento come [[Merge Sort]] perché utilizza molte chiamate ricorsive, quindi può causare problemi di memoria se si stanno ordinando grandi quantità di dati.
-   Non è deterministico, quindi potrebbe non ordinare gli stessi dati nello stesso modo ogni volta.

# Complessità

-   Nel caso migliore, quando l'algoritmo sceglie sempre l'elemento mediano come pivot, la complessità è O(n * log(n)), dove n è il numero di elementi nell'[[array]]. In questo caso, l'algoritmo è molto efficiente e veloce.

-   Nel caso peggiore, quando l'algoritmo sceglie sempre l'elemento più grande o più piccolo come pivot, la complessità è O(n^2), dove n è il numero di elementi nell'[[array]]. In questo caso, l'algoritmo diventa molto lento e meno efficiente.

-   Nella media, la complessità è O(n * log(n)), rendendo l'algoritmo quicksort una scelta comune per l'ordinamento di grandi quantità di dati.

| Caso Migliore | Caso Medio | Caso Peggiore |
| ------------- | ---------- | ------------- |
| O(nlogn)      | O(nlogn)   | O(n^2)        |

# Dimostrazione di Correttezza

Per dimostrare la correttezza del quicksort, dobbiamo dimostrare che l'algoritmo termina correttamente e che alla fine restituisce un [[array]] ordinato. Inoltre, dobbiamo dimostrare che il quicksort mantiene la proprietà dell'invariante di ciclo, ovvero che ogni iterazione del ciclo principale dell'algoritmo preserva l'ordinamento dell'array.

Supponiamo che l'array da ordinare sia A[1...n]. Il quicksort seleziona un elemento pivot e lo posiziona nella sua posizione corretta nell'array ordinato. L'algoritmo quindi ripete questo processo ricorsivamente per le due parti dell'array che si trovano a sinistra e a destra del pivot.

L'invariante di ciclo è che, in ogni iterazione del ciclo principale dell'algoritmo, l'array A[p...q] contiene gli elementi che sono maggiori o uguali al pivot e l'array A[q+1...r] contiene gli elementi che sono minori del pivot. Inoltre, l'array A[p...q] e l'array A[q+1...r] possono essere disposti in qualsiasi ordine, purché gli elementi in A[p...q] siano tutti minori o uguali al pivot e gli elementi in A[q+1...r] siano tutti maggiori del pivot.

Durante l'operazione di partizione, il quicksort sceglie un elemento pivot e divide l'array in due parti. L'algoritmo poi sposta gli elementi maggiori del pivot a destra del pivot e gli elementi minori del pivot a sinistra del pivot. Alla fine di questo processo, l'elemento pivot è posizionato nella sua posizione corretta nell'array ordinato.

In ogni passaggio ricorsivo, il quicksort applica l'operazione di partizione alle due parti dell'array. L'invariante di ciclo viene mantenuta in ogni passaggio ricorsivo e alla fine l'intero array viene ordinato.

# Dimostrazione complessità al caso medio

Supponiamo di avere un array A[1...n] da ordinare. In ogni passaggio dell'algoritmo, il quicksort sceglie un elemento pivot e suddivide l'array in due parti. La scelta del pivot è casuale (nella versione randomizzata) e ogni elemento ha la stessa probabilità di essere scelto come pivot.

In media, il pivot divide l'array in due parti di dimensioni simili. Supponiamo che il pivot divida l'array in due parti di dimensioni p e q, dove p+q=n. Il numero di confronti necessari per ordinare l'array A[1...n] è dato dalla somma del numero di confronti necessari per ordinare le due parti A[1...p] e A[p+1...n], più il numero di confronti necessari per posizionare il pivot nella sua posizione corretta nell'array ordinato.

In media, il numero di confronti necessari per posizionare il pivot nella sua posizione corretta è proporzionale alla dimensione dell'array, ovvero O(n). Inoltre, supponiamo che il quicksort sia correttamente implementato in modo da garantire che l'array sia diviso in due parti di dimensioni simili. In questo caso, il numero di confronti necessari per ordinare l'array A[1...n] è dato dalla somma del numero di confronti necessari per ordinare le due parti A[1...p] e A[p+1...n].

In media, la dimensione delle due parti è n/2. Pertanto, il numero di confronti necessari per ordinare l'array A[1...n] è dato dalla somma del numero di confronti necessari per ordinare due array di dimensione n/2, ovvero T(n) = 2T(n/2) + O(n).

Utilizzando il [[Master Theorem]], possiamo risolvere questa equazione di ricorrenza e ottenere T(n) = O(n log n). In particolare, la complessità al caso medio del quicksort è O(n log n), dove n è la dimensione dell'array da ordinare.