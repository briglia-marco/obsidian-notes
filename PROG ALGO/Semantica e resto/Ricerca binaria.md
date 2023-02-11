La **ricerca binaria** è un algoritmo di ricerca efficiente utilizzato per trovare un elemento in una *lista ordinata di elementi*. Il principio alla base della **ricerca binaria** è la divisione del problema in parti più piccole ([[Divide-et-impera]]). L'algoritmo inizia confrontando l'elemento che si sta cercando con l'elemento centrale della lista. Se l'elemento centrale è uguale all'elemento che si sta cercando, la ricerca è terminata con successo. In caso contrario, se l'elemento che si sta cercando è minore dell'elemento centrale, la ricerca continua nella metà inferiore della lista; se l'elemento che si sta cercando è maggiore dell'elemento centrale, la ricerca continua nella metà superiore della lista.

La ricerca binaria è molto più efficiente rispetto ad altri algoritmi di ricerca, poiché riduce il numero di confronti necessari per trovare l'elemento. La complessità temporale della ricerca binaria è O(log n), dove n è il numero di elementi nella lista.

La ricerca binaria è utilizzata in molte applicazioni informatiche, tra cui la ricerca di un elemento in un [[dizionario]], la ricerca di un elemento in un elenco di nomi, la ricerca di un elemento in un [[array]] ordinato, la ricerca di un elemento in una [[Hash map]] e molte altre.

# Algoritmo

```js
function binarySearch(array, target) {
  let left = 0;
  let right = array.length - 1;
  
  while (left <= right) {
    let middle = Math.floor((left + right) / 2);
    if (array[middle] === target) {
      return middle;
    } else if (array[middle] < target) {
      left = middle + 1;
    } else {
      right = middle - 1;
    }
  }
  return -1;
}

//algoritmo ricorsivo
function binarySearchRecursive(array, target, left, right) {
  if (left > right) {
    return -1;
  }
  let middle = Math.floor((left + right) / 2);
  if (array[middle] === target) {
    return middle;
  } else if (array[middle] < target) {
    return binarySearchRecursive(array, target, middle + 1, right);
  } else {
    return binarySearchRecursive(array, target, left, middle - 1);
  }
}

```