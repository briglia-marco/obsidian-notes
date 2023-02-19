Il lower bound di Ω(n log n) per il problema di ordinamento per confronti si può dimostrare utilizzando il cosiddetto "decision tree model". Questo modello consiste nell'immaginare un albero di decisione binario, dove ogni nodo interno rappresenta un confronto tra due elementi dell'[[array]] da ordinare e ogni foglia rappresenta una permutazione ordinata dell'array.

Supponiamo di avere un array di n elementi e di volerlo ordinare in modo crescente. Ogni permutazione ordinata corrisponde ad una foglia dell'albero di decisione. In questo albero, ogni nodo interno rappresenta un confronto tra due elementi dell'array e ha esattamente due figli, corrispondenti alle due possibili permutazioni che possono derivare dal confronto. Ogni percorso dall'alto verso il basso nell'albero di decisione rappresenta un confronto effettuato durante l'ordinamento dell'array.

Poiché ogni permutazione ordinata dell'array deve essere rappresentata da una foglia dell'albero, il numero di foglie deve essere almeno n!, poiché ci sono n! permutazioni ordinate possibili per un array di n elementi.

Ogni nodo interno dell'albero rappresenta un confronto tra due elementi dell'array. Poiché ogni confronto può avere solo due esiti possibili (l'uno è minore dell'altro, o viceversa), ogni nodo interno ha esattamente due figli. Quindi, il numero di nodi interni dell'albero deve essere almeno log n!, poiché un albero binario di altezza h ha al massimo 2^h foglie.

Applicando la formula di Stirling, possiamo calcolare che log n! è Ω(n log n), quindi il numero di confronti necessari per ordinare un array di n elementi deve essere almeno Ω(n log n), in base al decision tree model.

In altre parole, qualsiasi algoritmo di ordinamento per confronti che ordina un array di n elementi richiederà almeno Ω(n log n) confronti nel caso peggiore per completare l'ordinamento.

> l: numero di foglie
> h: altezza albero
> n: elementi
> n!: permutazioni dell'input 

> n! <= l <= 2^h 
> |
> |
> ==> h >= lg(n!) = Ω(n log n)