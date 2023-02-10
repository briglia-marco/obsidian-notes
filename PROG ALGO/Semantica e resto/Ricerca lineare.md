La ricerca lineare è un algoritmo di ricerca semplice che consiste nel controllare tutti gli elementi di una [[lista]] uno per uno per trovare un determinato elemento. La complessità temporale di questo algoritmo è O(n), dove n è il numero di elementi nella lista, poiché potrebbe essere necessario controllare tutti gli elementi per trovare l'elemento desiderato.

# Algoritmo

```js
function linearSearch(array, target) {
  for (let i = 0; i < array.length; i++) {
    if (array[i] === target) {
      return i;
    }
  }
  return -1;
}

function ricLin(array, target){
	var i = 0
	while(i <array.length && array[i] != target)
		i++
		return (i != array.length ? i : -1)
}
```