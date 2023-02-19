# Caratteristiche algoritmi Greedy (Golosi)

Un *Algoritmo Greedy (goloso)* fa sempre la scelta che sembra ottima in un determinato momento, ovvero fa la scelta localmente ottima, nella speranza che tale scelta porterà a una soluzione globalmente ottima. Gli algoritmi golosi non sempre riescono a trovare le soluzioni ottime, ma per molti problemi sono in grado di farlo. Con l'esempio che segue sul Problema dello [[Zaino]], vediamo che possiamo arrivare a una soluzione buona (non ottima) ma in tempi ragionevoli, mentre con lo [[Zaino]] Frazionario arriveremo a una soluzione ottima.

# Zaino Greedy

## Zaino non Frazionario

```js
function knapsackGreedy(values, weights, capacity) {
  // Calcola il rapporto valore/peso per ciascun oggetto
  let ratios = [];
  for (let i = 0; i < values.length; i++) {
    ratios[i] = values[i] / weights[i];
  }
  // Ordina gli oggetti in base al rapporto valore/peso in ordine decrescente
let sortedIndexes = Array.from(weights.keys()).sort((a, b) => ratios[b] - ratios[a]);

  // Inizia a riempire lo zaino
  let totalValue = 0;
  for (let i = 0; i < sortedIndexes.length; i++) {
    let index = sortedIndexes[i];
    if (weights[index] <= capacity && capacity > 0) {
      // Inserisce l'oggetto nello zaino e aggiorna la capacità residua
      totalValue += values[index];
      capacity -= weights[index];
    }
  }
  return totalValue;
}
```

## Zaino Frazionario

```js
function fractionalKnapsack(values, weights, capacity) {
  // Calcola il rapporto valore/peso per ciascun oggetto
  let ratios = [];
  for (let i = 0; i < values.length; i++) {
    ratios[i] = values[i] / weights[i];
  }
  // Ordina gli oggetti in base al rapporto valore/peso in ordine decrescente
  let sortedIndexes = Array.from(weights.keys()).sort((a, b) => ratios[b] - ratios[a]);

  // Inizia a riempire lo zaino
  let totalValue = 0;
  for (let i = 0; i < sortedIndexes.length; i++) {
    let index = sortedIndexes[i];
    if (weights[index] <= capacity && capacity > 0) {
      // Inserisce l'intero oggetto nello zaino e aggiorna la capacità residua
      totalValue += values[index];
      capacity -= weights[index];
    } else if (capacity > 0) {
      // Inserisce una frazione dell'oggetto nello zaino e aggiorna la capacità residua
      totalValue += capacity * ratios[index];
      capacity = 0;
    } else {
      // Lo zaino è pieno
      break;
    }
  }
  return totalValue;
}
```

