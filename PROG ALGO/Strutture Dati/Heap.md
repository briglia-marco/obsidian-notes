
<img src=https://i.imgur.com/UlW0FGd.png width="40%" />

# Caratteristiche

1.  Nodi figli sono sempre più piccoli del nodo padre    
2.  Nell’array associato gli indici dei figli sono rispettivamente (partendo da index=0):
	-    [2*i+1] per figlio di Sinistra 
	-    [2*i+2] per figlio di Destra
1.  La proprietà di base di un heap è che è un albero binario completo, ovvero un albero in cui tutti i livelli, tranne l'ultimo, sono completamente riempiti e tutti i nodi nell'ultimo livello sono allineati a sinistra.
2.  Un heap può essere implementato come un albero binario o un array.
3.  Esistono due tipi di heap: heap min e heap max. In un heap min, il valore minimo è sempre alla radice dell'albero, mentre in un heap max, il valore massimo è sempre alla radice dell'albero.

# Pro e Contro

I pro di un heap sono:

1) Tempo di accesso rapido al valore minimo (o massimo) in un heap min (o max): 
	-   poiché il valore minimo (o massimo) è sempre alla radice dell'albero, è possibile accedervi in tempo costante O(1).
2) Tempo di inserimento e rimozione rapido: 
	-   l'inserimento e la rimozione di un elemento richiedono tempo O(log n) in media, poiché è necessario solo ri-allineare l'albero per soddisfare la proprietà di heap.

I contro di un heap sono:

1) Tempo di ricerca lento: 
	-   poiché un heap è solo un albero binario completo, la ricerca di un elemento specifico richiede tempo O(n) in media.
2) Poca flessibilità di accesso: 
	-   un heap consente solo l'accesso al valore minimo (o massimo) in un heap min (o max), non consente di accedere facilmente ad altri elementi dell'albero.

# Algoritmi

## Classe Heap

```js
class Heap {
  constructor() {
    this.array = [];
  }

  // Funzione per ottenere il padre di un indice i
	getParentIndex(i) {
	    return Math.floor((i - 1) / 2);
	}

  // Funzione per ottenere il figlio sinistro di un indice i
	getLeftChildIndex(i) {
		return 2 * i + 1;
	}

  // Funzione per ottenere il figlio destro di un indice i
	getRightChildIndex(i) {
	    return 2 * i + 2;
	}

  // Funzione per inserire un elemento nell'heap
	insert(element) {
	    // Aggiungiamo l'elemento alla fine dell'array
	    this.array.push(element);
	    // Chiamiamo la funzione per ripristinare la proprietà dell'heap
	    this.maxHeapify(this.array.length - 1);
	}

	  // Funzione per ripristinare la proprietà di un max-heap  
	maxHeapify(i) {  
		// Calcoliamo gli indici dei figli  
		let leftChildIndex = this.getLeftChildIndex(i);  
		let rightChildIndex = this.getRightChildIndex(i);  
	  
		// Indice del figlio maggiore  
		let largestIndex = i;  
  
		// Se il figlio sinistro esiste ed è maggiore del padre  
		if (leftChildIndex < this.array.length && this.array[leftChildIndex] > this.array[largestIndex]) {  
		largestIndex = leftChildIndex;  
		}  
  
		// Se il figlio destro esiste ed è maggiore del padre  
		if (rightChildIndex < this.array.length && this.array[rightChildIndex] > this.array[largestIndex]) {  
		largestIndex = rightChildIndex;  
		}  
  
		// Se il figlio maggiore non è il padre  
		if (largestIndex !== i) {  
		// Scambiamo il padre con il figlio maggiore  
		[this.array[i], this.array[largestIndex]] = [this.array[largestIndex], this.array[i]];  
		// Chiamiamo la funzione per ripristinare la proprietà dell'heap  
		this.maxHeapify(largestIndex);  
		}  
	}

	// Metodo per estrarre un nodo con valore k dall'albero heap
	extractNodeWithValue(k) {
	  // Troviamo l'indice del nodo con valore k nell'array
		let nodeIndex = this.array.indexOf(k);
		if (nodeIndex === -1) {
		    // Se il nodo non esiste, restituiamo null
		    return null;
	  } else {
	//Sostituiamo il valore del nodo trovato con il valore massimo dell'albero heap
		    this.array[nodeIndex] = this.array[this.array.length - 1];
		    // Rimuoviamo il valore massimo dall'albero heap
		    this.array.pop();
		    // Ripristiniamo la proprietà di max-heap
		    this.maxHeapify(nodeIndex);
		    // Restituiamo il valore del nodo estratto
		    return k;
		}
	}

	// Algoritmo HeapSort in JavaScript
	function heapSort(array) {
	  // Costruiamo un albero heap a partire dall'array da ordinare
	  let heap = new MaxHeap(array);
		// Estrarre il valore massimo dall'albero heap e inserirlo alla fine dell'array ordinato
	  for (let i = array.length - 1; i >= 0; i--) {
	    array[i] = heap.extractMax();
	  }
	  // Restituiamo l'array ordinato
	  return array;
	}

}

```