# Pseudocodice

```js
function selectionSort(A: array of items)
   for i = 0 to length[A]-1
       minIndex = i 
       for j = i+1 to length[A] 
           if A[j] < A[minIndex] 
           //"minIndex" viene aggiornato con l'indice corrente "j"
               minIndex = j  
       end for
       //Gli elementi "A[i]" e "A[minIndex]" vengono scambiati 
       swap A[i] and A[minIndex] 
   end for
end procedure
```

# Pro e Contro

Vantaggi:

-   È semplice da implementare e capire, poiché utilizza solo due cicli.
-   È stabile, ovvero mantiene l'ordine relativo degli elementi uguali.
-   Utilizza poco spazio extra, poiché non richiede array o strutture dati aggiuntive.

Svantaggi:

-   Non è molto efficiente per grandi set di dati.
-   Non è un algoritmo adatto per l'elaborazione in tempo reale poiché la sua complessità è elevata
-   In alcune situazioni potrebbe essere più lento dell'algoritmo di ordinamento per inserimento.

# Complessità

La complessità è sempre O(n^2) ad ogni caso