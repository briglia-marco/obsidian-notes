
![](https://i.imgur.com/W1cgpBR.png)

# Caratteristiche

Una pila ('stack' in inglese) è una struttura dati di tipo **LIFO (Last In First Out)**, che significa che l'ultimo elemento inserito è il primo a essere rimosso. È simile a una pila di piatti, dove l'ultimo piatto posato è il primo a essere preso.

Le pile sono utilizzate in molte applicazioni, come l'elaborazione delle espressioni, l'implementazione di chiamate di funzioni ricorsive, la navigazione della cronologia del browser, etc.

In molti linguaggi di programmazione, le pile possono essere implementate utilizzando [[array]] o [[liste]], ma anche tramite classi o strutture dati specifiche. Ad esempio, in Python, è possibile utilizzare la classe "list" per implementare una pila, ma esiste anche la classe "collections.deque" che fornisce un'implementazione più efficiente della pila.

Le operazioni di base su una pila sono la "push" (inserimento di un elemento nella pila) e la "pop" (rimozione dell'elemento in cima alla pila). Inoltre, è anche possibile accedere all'elemento in cima alla pila senza rimuoverlo, utilizzando l'operazione "peek".

# Metodi pile

```js
let stack = [];

// Push: inserisce un elemento nella pila
function push(element) {
  stack.push(element);
}

// Pop: rimuove e restituisce l'elemento in cima alla pila
function pop() {
  return stack.pop();
}

// Peek: restituisce l'elemento in cima alla pila senza rimuoverlo
function peek() {
  return stack[stack.length - 1];
}
```

>Esempio di utilizzo

```js
let stack = [];
push(1);
push(2);
push(3);

console.log(stack); // Output: [1, 2, 3]

console.log(peek()); // Output: 3

console.log(pop()); // Output: 3

console.log(stack); // Output: [1, 2]
```