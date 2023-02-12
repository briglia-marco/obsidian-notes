# Vantaggi

Nella'analisi del comportamento di [[Quick Sort]] nel caso medio, abbiamo fatto l'ipotesi che tutte le permutazioni dei numeri di input fossero ugualmente probabili. 
Nella pratica, però, non possiamo aspettarci che questo sia sempre vero. A volte è possibile aggiungere una randomizzazione a un algoritmo per ottenere una buona prestazione attesa con tutti gli input. Molti considerano la versione randomizzata di [[Quick Sort]] come l'algoritmo di ordinamento di elezione per input sufficientemente grandi.
Possiamo randomizzare il nostro algoritmo permutando esplicitamente l'input. Potremmo fare la stessa cosa anche per quicksort; invece adotteremo un altro metodo di randomizzazione, detto *campionamento casuale*, che ci consente di semplificare l'analisi. Anzichè utilizzare sempre `A[end]` come pivot, utilizzeremo un elemento scelto a caso dal sottoarray `A[start..end]`. Per fare questo, scambieremo l'elemento `A[end]` con un elemento scelto a caso da `A[start..end]`. Questa modifica, con la quale campioniamo a caso l'intervallo p,...,r, ci assicura che l'elemento pivot `x = A[end]` avrà la stessa probabilità di essere uno qualsiasi degli `end-start+1` elementi del sottoarray. Poichè il pivot viene scelto a caso, ci aspettiamo che la ripartizione dell'[[array]] di input sia ben bilanciata in media.
Le modifiche da apportare a PARTITION e QUICKSORT sono modeste. Nella nuova procedura di partizionamento, implementiamo semplicemente lo scambio prima dell'effettivo partizionamento.

## Partition

```js
function partition(arr, start, end) {
  let pivot = arr[end];
  let partitionIndex = start - 1;
  for (let i = start; i <= end - 1; i++) {
    if (arr[i] <= pivot) {
      partitionIndex++;
      [arr[partitionIndex], arr[i]] = [arr[i], arr[partitionIndex]];
    }
  }
  [arr[partitionIndex + 1], arr[end]] = [arr[end], arr[partitionIndex + 1]];
  return partitionIndex + 1;
}
```

>Il metodo "partition" è utilizzato per suddividere gli elementi di un array in base alla loro posizione rispetto a un pivot. In questo esempio, il pivot è l'ultimo elemento dell'array. Il metodo scorre l'array e ogni volta che incontra un elemento che è minore o uguale al pivot, lo scambia con l'elemento all'indice successivo di `partitionIndex`. Al termine del ciclo, il pivot viene scambiato con l'elemento all'indice successivo di `partitionIndex`, che rappresenta la posizione del pivot nell'array ordinato. Il metodo restituisce quindi l'indice del pivot.

## Random

```js
function getRandom(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

```

> Ovviamente passiamo alla nostra funzione `start` e `end`.

## Randomized-Partition

```js
function randomizedPartition(arr, start, end) {
	var i = getRandom(start,end)
	[arr[end], arr[i]] = [arr[i], arr[end]]
	return partition(arr, start, end)
}
```

> Il nuovo Quicksort chiama `Randomized-Partition`, anzichè `Partition`.

## Randomized-Quicksort

```js
function randomizedQuickSort(arr, start, end) {
  if (start < end) {
    let partitionIndex = randomizedPartition(arr, start, end);
    randomizedQuickSort(arr, start, partitionIndex - 1);
    randomizedQuickSort(arr, partitionIndex + 1, end);
  }
}
```