# Pseudocodice

```js
function mergesort(A: array di elementi, inizio: indice, fine: indice)
   //se ci sono ancora elementi da ordinare
   if(inizio < fine)
       //calcoliamo la metà dell'array
       var metà := (inizio + fine) / 2
       //ordiniamo la prima metà dell'array
       mergesort(A, inizio, metà)
       //ordiniamo la seconda metà dell'array
       mergesort(A, metà + 1, fine)
       //uniamo le due metà ordinate
       merge(A, inizio, metà, fine)
   fine procedura

function merge(A: array di elementi, inizio: indice, metà: indice, fine: indice)
   //lunghezza delle due metà da unire
   lunghezzaSx := metà - inizio + 1
   lunghezzaDx := fine - metà

   //creiamo due array temporanei per la prima e la seconda metà
   sinistra[1..lunghezzaSx + 1]
   destra[1..lunghezzaDx + 1]

   //copiamo gli elementi nei due array temporanei
   per i := 1 a lunghezzaSx
       sinistra[i] := A[inizio + i - 1]
   per j := 1 a lunghezzaDx
       destra[j] := A[metà + j]
      
   //inizializziamo i, j, k come indici per sinistra, destra e A
   i := 1
   j := 1
   k := inizio

   //uniamo i due array temporanei ordinati in A
   per k := inizio a fine
       if i > lunghezzaSx
           //se abbiamo finito con la prima metà, aggiungiamo gli elementi rimanenti della seconda metà
           A[k] := destra[j]
           j := j + 1
       altrimenti se j > lunghezzaDx
           //se abbiamo finito con la seconda metà, aggiungiamo gli elementi rimanenti della prima metà
           A[k] := sinistra[i]
           i := i + 1
       altrimenti se sinistra[i] < destra[j]
           //se è minore, lo aggiungiamo ad A
           A[k] := sinistra[i]
           i := i + 1
       altrimenti
           //altrimenti, l'elemento nell'array destra è minore e lo aggiungiamo ad A
           A[k] := destra[j]
           j := j + 1
   return
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

