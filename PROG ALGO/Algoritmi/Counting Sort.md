# Introduzione

Il Counting Sort è un algoritmo di ordinamento basato sulla distribuzione dei valori nell'input. Funziona contando il numero di volte che ogni valore appare nell'input e utilizzando queste informazioni per stabilire la posizione di ciascun elemento nell'output ordinato.

Il Counting Sort è utilizzato quando i valori nell'input sono limitati a un intervallo noto e fisso di valori possibili. In altre parole, se i valori nell'input appartengono a un insieme finito di valori distinti, si può utilizzare il Counting Sort. Questo lo rende particolarmente utile per la ordinazione di array di interi o di valori che possono essere facilmente mappati su un intervallo limitato di interi.

Il Counting Sort è molto efficiente in termini di tempo di esecuzione, poiché non ha bisogno di confrontare o scambiare elementi. Tuttavia, richiede molto spazio extra per archiviare il conteggio dei valori, rendendolo meno efficiente in termini di utilizzo della memoria rispetto ad altri algoritmi di ordinamento come l'ordinamento a bolle o il quick sort.


# Pseudocodice

```js
function countingSort(arr, k)
    // Creiamo un array di contatori di lunghezza k+1
    countArr = new int[k+1]

    // Inizializziamo tutti i valori del contatore a 0
    for i = 0 to k
        countArr[i] = 0

    // Contiamo quante volte ogni elemento appare nell'array
    for i = 0 to length(arr) - 1
        countArr[arr[i]] = countArr[arr[i]] + 1

    // Sommiamo i contatori per ottenere la posizione di ogni elemento nell'array ordinato
    for i = 1 to k
        countArr[i] = countArr[i] + countArr[i-1]
        
    // Creiamo un array di output
    output = new int[length(arr)]

    // Inseriamo gli elementi nell'array di output nella posizione corretta in base al contatore
    for i = length(arr) - 1 downto 0
        output[countArr[arr[i]]-1] = arr[i]
        countArr[arr[i]] = countArr[arr[i]] - 1
        
    // Copiamo gli elementi ordinati nell'array originale
    for i = 0 to length(arr) - 1
        arr[i] = output[i]
```

# Pro e Contro

Pro:

-   Il counting sort è un algoritmo stabile e in-place
-   Ha una complessità O(n+k) dove n è il numero di elementi e k è la gamma dei valori degli elementi, rendendolo molto efficiente per array con valori limitati e distribuiti uniformemente
-   È facile da implementare

Contro:

-   Non funziona per array con valori negativi
-   Non è adatto per array con valori distribuiti in modo non uniforme.    
-   Non è adatto per array con una gamma di valori molto grande in quanto richiede un array di conteggio di dimensioni uguali alla gamma dei valori degli elementi.

# Complessità ai vari casi

-   La complessità del counting sort è O(n+k) nel caso migliore, dove n è il numero di elementi e k è la gamma dei valori degli elementi.

-   In caso peggiore, quando gli elementi non sono distribuiti uniformemente, la complessità diventa O(n^2)

| Caso Migliore | Caso Medio | Caso Peggiore |
| ------------- | ---------- | ------------- |
| O(n+k)      | O(n+k)   | O(n^2)        |
