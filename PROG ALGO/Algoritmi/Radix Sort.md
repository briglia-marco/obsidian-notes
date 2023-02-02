# Pseudocodice

```js
function radixSort(arr, d)

for i = 1 a d
/*utilizza un algoritmo di ordinamento stabile
per ordinare arr in base alla i-esima cifra */*
(ex. countingSort(...))
```
-   Gli elementi in base ad una chiave. In questo caso, la chiave è il numero di cifre dell'elemento. Si parte dalla cifra meno significativa (unità) e si procede verso la più significativa (migliaia, milioni, ecc.).

-   Il parametro `d` rappresenta il numero di cifre del numero più grande nell'array.

-   Il ciclo `for` esterno esegue l'operazione di ordinamento `d` volte, una volta per ogni cifra dei numeri nell'array. All'interno del ciclo for viene utilizzato un algoritmo di ordinamento stabile, come ad esempio [[Counting Sort]], per ordinare gli elementi dell'array in base alla cifra corrente. 

# Pro e Contro
 
Vantaggi:

-   Tempo di esecuzione efficiente con una complessità O(nk)
-   Algoritmo stabile che mantiene l'ordine relativo degli elementi con lo stesso valore di chiave
-   Funziona bene con array di numeri interi di dimensioni grandi

Svantaggi:

-   Richiede una quantità significativa di spazio di memoria per gli array di contatori
-   Limitato all'ordinamento di numeri interi, non può essere utilizzato per ordinare stringhe o oggetti
-   Meno efficiente quando i numeri hanno un gran numero di cifre

# Complessità

- La complessità del radix sort dipende dal numero di cifre del numero più grande nell'array. In termini generali, la complessità è O(nk), dove n è il numero di elementi nell'array e k è il numero di cifre del numero più grande nell'array.

- In caso di un array di numeri interi con un numero di cifre piccole, la complessità sarà molto bassa e l'algoritmo sarà molto veloce. Ad esempio, se l'array contiene solo numeri a due cifre, la complessità sarà O(n).

- D'altra parte, se l'array contiene numeri con un gran numero di cifre, la complessità aumenterà e l'algoritmo sarà meno efficiente. Ad esempio, se l'array contiene numeri a dieci cifre, la complessità sarà O(10n)

- In generale, la complessità del radix sort dipende dal numero di cifre del numero più grande nell'array, quindi più cifre ha il numero più grande, più tempo ci vorrà per ordinare l'array.

