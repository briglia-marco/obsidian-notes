# Definizione

Il problema dello zaino (in inglese, "knapsack problem") è un noto problema di ottimizzazione combinatoria che consiste nel determinare *la combinazione di oggetti di peso e valore diversi che possono essere inseriti in uno zaino di capacità limitata*, in modo da massimizzare il valore totale degli oggetti.

In altre parole, dato uno zaino con una capacità massima di peso e un insieme di oggetti, ciascuno con un proprio peso e valore, il problema consiste nel determinare quali oggetti scegliere da inserire nello zaino, in modo da massimizzare il valore totale degli oggetti, rispettando la capacità massima dello zaino.

Esistono diverse varianti del problema dello zaino, in base alle restrizioni e agli obiettivi specifici. Ad esempio, si possono avere restrizioni sul numero di oggetti che si possono scegliere, oppure si può cercare di minimizzare il peso totale degli oggetti, anziché massimizzare il valore.

# Soluzione con [[Programmazione dinamica]]

```js 
function knapsack(values, weights, capacity) {
  // inizializza la variabile n con la lunghezza dei vettori values e weights
  const n = values.length;
  // crea una matrice di dimensioni (n+1) x (capacity+1) con tutti i valori a 0
  const matrix = new Array(n + 1).fill().map(() => new Array(capacity + 1).fill(0));

  // riempi la matrice riga per riga, partendo dalla seconda riga
  for (let i = 1; i <= n; i++) {
    // considera l'oggetto i-1 (il primo oggetto ha indice 0)
    const currentWeight = weights[i - 1];
    const currentValue = values[i - 1];

    for (let j = 1; j <= capacity; j++) {
      // se l'oggetto corrente non può essere incluso nello zaino, prendi il valore
      // della cella sopra, corrispondente alla stessa capacità ma senza l'oggetto corrente
      if (currentWeight > j) {
        matrix[i][j] = matrix[i - 1][j];
      } else {
        // altrimenti, scegli il massimo tra il valore della cella sopra (senza l'oggetto corrente)
        // e il valore che si otterrebbe includendo l'oggetto corrente, che corrisponde al suo valore
        // sommato al valore massimo ottenibile con la capacità residua
        matrix[i][j] = Math.max(matrix[i - 1][j], currentValue + matrix[i - 1][j - currentWeight]);
      }
    }
  }

  // il valore massimo ottenibile è nella cella in fondo a destra della matrice
  return matrix[n][capacity];
}

```

> In questo esempio, `values` e `weights` sono due array che contengono rispettivamente i valori e i pesi degli oggetti, mentre `capacity` rappresenta la capacità massima dello zaino. La funzione `knapsack` restituisce il valore massimo che si può ottenere con la combinazione di oggetti e capacità di zaino specificate.
  La matrice `matrix` ha `n+1` righe e `capacity+1` colonne, per permettere la memorizzazione dei casi base (nessun oggetto e nessuna capacità) e l'accesso agli indici a partire da 1. La cella `(i,j)` della matrice rappresenta il valore massimo che si può ottenere considerando i primi `i` oggetti e una capacità massima di `j`. La cella `matrix[i-1][j-weights[i-1]]` rappresenta il valore massimo che si può ottenere considerando i primi `i-1` oggetti e una capacità massima di `j-weights[i-1]`, nel caso in cui si scelga di includere l'oggetto corrente.