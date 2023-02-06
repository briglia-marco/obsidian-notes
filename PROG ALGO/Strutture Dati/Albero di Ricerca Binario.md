
<img src=https://i.imgur.com/fZPVrcb.png width="80%" />

# Cratteristiche

-  Sono [[Alberi Binari]] con le seguenti accortezze:
	1) Nodi più piccoli del nodo padre sulla sinistra
	2) Nodi più grandi del nodo padre sulla destra

# Pro e Contro

I pro degli alberi binari di ricerca sono:

-   Velocità di ricerca: la ricerca di un elemento in un albero binario di ricerca è molto più veloce rispetto ad una ricerca sequenziale in una lista non ordinata.
-   Utilizzo efficiente dello spazio: gli alberi binari di ricerca utilizzano spazio in modo efficiente, poiché ogni nodo contiene solo un elemento.
-   Facilità di implementazione: gli alberi binari di ricerca sono semplici da implementare e comprendere.

I contro degli alberi binari di ricerca sono:

-   Dipendenza dall'ordine di inserimento: se gli elementi vengono inseriti in ordine casuale, l'albero può diventare squilibrato e le prestazioni possono deteriorarsi.    
-   Richiede un po' più di codice per implementare rispetto ad una semplice lista o matrice.
-   Non è adatto a tutti i tipi di dati: gli alberi binari di ricerca funzionano meglio con dati ordinati o ordinabili.

# Algoritmi

## Ricerca

```js
function search(node, value):
    if node is null or node.value == value:
        return node
    if value < node.value:
        return search(node.left, value)
    else:
        return search(node.right, value)
```

## Inserimento

```js
function insert(node, value):
    if node is null and value!=node.value:
        return new Node(value)
    if value < node.value:
        node.left = insert(node.left, value)
    else if value> node.value:
        node.right = insert(node.right, value)
    return node
```

## Cancellazione

```js
function delete(node, value):
    //se il nodo è nullo, restituisce null
    if node is null:
        return null

//se il valore da cancellare è minore del valore del nodo corrente, continua la ricerca nel sottoalbero sinistro
    if value < node.value:
        node.left = delete(node.left, value)

//se il valore da cancellare è maggiore del valore del nodo corrente, continua la ricerca nel sottoalbero destro
    elif value > node.value:
        node.right = delete(node.right, value)

//se il valore del nodo corrente è quello da cancellare
    else:
        //se il nodo non ha figli, esso viene eliminato
        if node.left is null and node.right is null:
            node = null
        //se il nodo ha solo un figlio, esso viene sostituito dal suo figlio
        elif node.left is null:
            node = node.righ
        elif node.right is null:
            node = node.left

//se il nodo ha due figli, esso viene sostituito dal nodo più piccolo del suo sottoalbero destro, e quel nodo viene poi eliminato dall'albero
        else:
            minNode = findMin(node.right)
            node.value = minNode.value
            node.right = delete(node.right, minNode.value)
    return node
    

function findMin(node):
    //trova il nodo più piccolo del sottoalbero destro del nodo corrente
    while node.left is not null:
        node = node.left
    return node
```

## Visita in Ordine

```js
function inOrder(node):
    if node is not null:
        inOrder(node.left)
        print(node.value)
        inOrder(node.right)
```
