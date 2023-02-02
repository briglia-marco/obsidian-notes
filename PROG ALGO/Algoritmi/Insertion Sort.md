# Pseudocodice
```js
function insertionSort(A: array of item) 
   for i = 1 to length[A] 
       j = i 
       while j > 0 and A[j-1] > A[j] //controlla se j>0 e se l'elemento prima di "A[j]" è maggiore di "A[j]"
           swap A[j] and A[j-1] 
           j = j - 1 
		// j viene decrementato di 1 per continuare il confronto con l'elemento precedente
   end procedure
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
| O(n)      | O(n^2)   | O(n^2)        |
