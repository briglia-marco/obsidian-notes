
![](https://lh6.googleusercontent.com/GinDJ4EDg47dea9Zf9QHFahWrfAY2NSjL0Q2ehH4YbIaXJ4nVoLY8DLwNZnkkZTruQ7dEDysEWzquHuxb3OW67xEObV6Mw7P8oZwMHnIFbtVKYFLfFBnEaB6YsP8vaF_BUToyH2QBBwdXZI8DfjXr0o)

# Caratteristiche

Un albero 2-3 è un albero nel quale ogni nodo interno a 2 o 3 figli e tutti i cammini radice/foglia hanno la stessa lunghezza.
I valori sono posizionati in ordine crescente come su un albero di ricerca binario.

# Pro e Contro

Pro:

-   Elevata capacità di memorizzazione: gli alberi 2-3 possono memorizzare grandi quantità di dati, poiché ogni nodo può contenere fino a tre chiavi.
-   Elevata efficienza di ricerca: la ricerca di un elemento in un albero 2-3 ha una complessità temporale O(log n) in media.
-   Elevata tolleranza alla frammentazione: gli alberi 2-3 possono essere utilizzati in sistemi di memorizzazione su disco, poiché la loro struttura consente di gestire facilmente la frammentazione dei dati

Contro:

-   Elevata complessità: gli alberi 2-3 sono più complessi da implementare rispetto ad altri tipi di alberi, poiché richiedono una maggiore attenzione alla gestione dei nodi con più di due chiavi.
-   Maggiore utilizzo di risorse: gli alberi 2-3 richiedono più memoria rispetto ad altri tipi di alberi, poiché ogni nodo può contenere fino a tre chiavi.

# Algoritmi

## Search

```js
function search(node, key) {
  // Se il nodo attuale è una foglia, si scorre l'elenco delle chiavi del nodo
  if (node.isLeaf) {
    for (let i = 0; i < node.numKeys; i++) {
      // Se la chiave è stata trovata, si restituisce il relativo valore
      if (node.keys[i] === key) {
        return node.values[i];
      }
    }
    // Se la chiave non è stata trovata, si restituisce null
    return null;
  } else {
    // Se il nodo attuale non è una foglia, si confronta la chiave da cercare con le chiavi del nodo
    for (let i = 0; i < node.numKeys; i++) {
      if (key < node.keys[i]) {
        // Se la chiave è minore della chiave corrente, si continua la ricerca nel sottoalbero corrispondente
        return search(node.children[i], key);
      }
      // Se la chiave è maggiore o uguale all'ultima chiave del nodo, si continua la ricerca nell'ultimo sottoalbero
      if (i === node.numKeys - 1) {
        return search(node.children[i + 1], key);
      }
    }
  }
} 
```


## Insert

```js
//funzione per inserire una chiave e un valore in un albero 2-3
function insert(node, key, value) {
  //se il nodo corrente è una foglia
  if (node.isLeaf) {
    //se ci sono meno di 2 chiavi nel nodo, si inserisce la chiave e il valore
    if (node.numKeys < 2) {
      insertKeyValue(node, key, value);
    }
    //altrimenti, si divide il nodo
    else {
      splitLeafNode(node, key, value);
    }
  } 
  //se il nodo corrente non è una foglia
  else {
    for (let i = 0; i < node.numKeys; i++) {
      //se la chiave da inserire è minore della chiave corrente
      if (key < node.keys[i]) {
        //continuare l'inserimento nel sottoalbero corrispondente
        insert(node.children[i], key, value);
        //se il sottoalbero diventa pieno, si divide
        if (node.children[i].numKeys === 3) {
          splitInternalNode(node, i);
        }
        return;
      }
    }
    //se la chiave è maggiore o uguale all'ultima chiave del nodo, continuare l'inserimento nell'ultimo sottoalbero
    insert(node.children[node.numKeys], key, value);
    //se l'ultimo sottoalbero diventa pieno, si divide
    if (node.children[node.numKeys].numKeys === 3) {
      splitInternalNode(node, node.numKeys);
    }
  }
}
```


## Split

```js
// Funzione per dividere un nodo foglia
function splitLeafNode(node, key, value) {
  // Crea un nuovo nodo
  var newNode = createNewLeafNode();
  // Trova la posizione in cui inserire la nuova chiave nel nodo originale
  var insertionIndex = findInsertionIndex(node, key);
  // Sposta tutte le chiavi successive all'indice di inserimento
  for (var i = node.numKeys - 1; i >= insertionIndex; i--) {
    node.keys[i + 1] = node.keys[i];
    node.values[i + 1] = node.values[i];
  }
  // Inserisce la nuova chiave e il valore
  node.keys[insertionIndex] = key;
  node.values[insertionIndex] = value;
  node.numKeys++;
  // Divide le chiavi del nodo originale tra il nodo originale e il nuovo nodo
  var medianIndex = Math.floor((node.numKeys + 1) / 2);
  newNode.numKeys = node.numKeys - medianIndex;
  node.numKeys = medianIndex;
  for (var i = 0; i < newNode.numKeys; i++) {
    newNode.keys[i] = node.keys[medianIndex + i];
    newNode.values[i] = node.values[medianIndex + i];
  }
  // Aggiorna il puntatore al successivo del nuovo nodo
  newNode.next = node.next;
  node.next = newNode;
  // Ritorna la chiave mediana per l'inserimento nel nodo padre
  return node.keys[medianIndex];
}
```

### Schema Processo di Split

<img src="https://i.imgur.com/uJGalsG.jpg" alt="Schema Split" width="50%" height="50%" />

