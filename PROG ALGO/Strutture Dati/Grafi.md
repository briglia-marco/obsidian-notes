
![](https://i.imgur.com/mkQpO7z.png)

# Caratteristiche

Un grafo è una struttura dati composta da nodi e archi. I nodi rappresentano gli elementi del grafo, mentre gli archi rappresentano le relazioni tra questi elementi

## Diversi concetti fondamentali

### Diretti o non diretti

-   Gli archi di un grafo diretto hanno una direzione, mentre quelli di un grafo non diretto non ne hanno.

### Pesati o non pesati

-   Gli archi di un grafo pesato hanno un peso associato, mentre quelli di un grafo non pesato non ne hanno.

### Connessi o sconnessi 

-   Un grafo è connesso se esiste almeno un percorso tra qualsiasi coppia di nodi; in caso contrario, è sconnesso.

### Ciclici o aciclici 

-   Un grafo è ciclico se esiste almeno un percorso che inizia e finisce nello stesso nodo; in caso contrario, è aciclico.

### Regolare o irregolare

-   Un grafo è regolare se tutti i nodi hanno lo stesso grado (cioè, il numero di archi incidenti su ogni nodo); in caso contrario, è irregolare.

### Adiacenza

-   Due nodi sono adiacenti se esiste un arco che li connette

### Cammino e Percorso

-   Un cammino è una sequenza di nodi e arche che iniziano e finiscono in nodi specifici, mentre un percorso è un cammino i cui nodi sono distinti

### Grafo Bipartito

-   un grafo bipartito è un grafo in cui i nodi possono essere divisi in due gruppi in modo tale che non esistono archi tra i nodi di uno stesso gruppo

### Algoritmi di percorso

-   esistono diversi algoritmi per trovare il percorso più breve o più lungo tra due nodi in un grafo, come l'algoritmo di Dijkstra o l'algoritmo di Bellman-Ford.

# Pro e Contro

Pro:

-   Possono rappresentare relazioni complesse in modo intuitivo e facilmente comprensibile.    
-   Sono utili per risolvere problemi di percorso, ad esempio, trovare il percorso più breve tra due nodi in un grafo.
-   Possono essere utilizzati per rappresentare reti, come le reti sociali o le reti di trasporto.
-   Sono utili per la rappresentazione di problemi di ottimizzazione, come il [[problema del commesso viaggiatore]].

Contro:

-   Possono essere difficili da implementare e gestire per grafi di grandi dimensioni.    
-   Possono richiedere una grande quantità di memoria per la rappresentazione dei dati.
-   Possono essere computazionalmente costosi da elaborare, soprattutto per algoritmi di percorso più avanzati.
-   Possono essere meno efficaci per rappresentare dati relazionali con cardinalità elevata.

# Algoritmi


## Bellman-Ford

*Il Bellman-Ford è un algoritmo utilizzato per trovare il percorso più breve tra un nodo sorgente e tutti gli altri nodi in un grafo con pesi negativi.*

```js
function bellmanFord(grafo, partenza) {
  // Creiamo un array di distanze con valore iniziale Infinito per ogni vertice
  let distanze = Array(grafo.length).fill(Infinity);
  // La distanza del vertice di partenza è 0
  distanze[partenza] = 0;

  // Ripetiamo il loop V-1 volte, dove V è il numero di vertici
  for (let i = 0; i < grafo.length - 1; i++) {
    // Per ogni vertice
    for (let j = 0; j < grafo.length; j++) {
      // E per ogni suo vicino
      for (let k = 0; k < grafo[j].length; k++) {
        let vicino = grafo[j][k];
        // Se la distanza attraverso questo vicino è minore della distanza corrente del vicino
        if (distanze[j] + vicino.peso < distanze[vicino.vertice]) {
          // Aggiorniamo la distanza del vicino
          distanze[vicino.vertice] = distanze[j] + vicino.peso;
        }
      }
    }
  }

  // Verifichiamo se esiste un ciclo negativo
  for (let i = 0; i < grafo.length; i++) {
    for (let j = 0; j < grafo[i].length; j++) {
      let vicino = grafo[i][j];
      // Se la distanza attraverso questo vicino è ancora minore della distanza del vicino
      if (distanze[i] + vicino.peso < distanze[vicino.vertice]) {
        // Restituiamo false, in quanto esiste un ciclo negativo
        return false;
      }
    }
  }

  // Altrimenti restituiamo le distanze da ogni vertice al vertice di partenza
  return distanze;
}
```

>La complessità di questo algoritmo è di `O(V * E)`, dove `V` è il numero di vertici e `E` è il numero di archi. Questo rende l'algoritmo molto efficiente per grafi densi, ma inefficente per grafi molto sparsi.


## Dijkstra

*L'algoritmo di Dijkstra è un algoritmo di shortest path (percorso più breve) utilizzato per trovare il percorso più breve tra un nodo sorgente e tutti gli altri nodi in un grafo con pesi positivi.
Funziona utilizzando una coda di priorità per mantenere l'ordine dei nodi da visitare e una volta che un nodo è stato visitato, non viene più considerato.*

```js
function dijkstra(grafo, partenza) {
  // Creiamo un array di distanze con valore iniziale Infinito per ogni vertice
  let distanze = Array(grafo.length).fill(Infinity);
  // La distanza del vertice di partenza è 0
  distanze[partenza] = 0;

  // Creiamo una coda di priorità per tenere traccia dei vertici da esplorare
  let coda = new PriorityQueue();
  coda.enqueue(partenza, 0);

  // Creiamo un array di visite per tenere traccia dei vertici già esplorati
  let visite = Array(grafo.length).fill(false);

  // Finche la coda non è vuota
  while (!coda.isEmpty()) {
    // Preleviamo il vertice con la distanza minima dalla coda
    let attuale = coda.dequeue();
    let vertice = attuale.vertice;
    let peso = attuale.peso;

    // Se questo vertice non è ancora stato visitato
    if (!visite[vertice]) {
      // Lo marchiamo come visitato
      visite[vertice] = true;

      // Per ogni vicino di questo vertice
      for (let i = 0; i < grafo[vertice].length; i++) {
        let vicino = grafo[vertice][i];
        // Se la distanza attraverso questo vicino è minore della distanza corrente del vicino
        if (distanze[vertice] + vicino.peso < distanze[vicino.vertice]) {
          // Aggiorniamo la distanza del vicino
          distanze[vicino.vertice] = distanze[vertice] + vicino.peso;
          // E inseriamo il vicino nella coda
          coda.enqueue(vicino.vertice, distanze[vicino.vertice]);
        }
      }
    }
  }
  // Restituiamo le distanze da ogni vertice al vertice di partenza
  return distanze;
}

```

>La complessità di questo algoritmo è di `O(E + V * log V)`, dove `V` è il numero di vertici e `E` è il numero di archi. Questo rende l'algoritmo molto efficiente per grafi molto sparsi, ma inefficente per grafi densi.

>> Nota: Questo codice utilizza una coda di priorità (`PriorityQueue`), che non è inclusa nella libreria standard di JavaScript. Sarà necessario implementarla o utilizzare una libreria esterna.

# Ordinamento topologico

L'ordinamento topologico è un algoritmo utilizzato per ordinare i nodi di un grafo diretto aciclico (DAG) in modo tale che ogni arco del grafo punti da un nodo precedente a un nodo successivo nell'ordinamento. In altre parole, l'ordinamento topologico definisce un ordinamento lineare dei nodi del DAG in cui ogni nodo è disposto prima di tutti i suoi discendenti.

> Guardo quale nodo ha solo archi uscenti e da lì cerco un cammino che unisca tutti i nodi dell'albero.


