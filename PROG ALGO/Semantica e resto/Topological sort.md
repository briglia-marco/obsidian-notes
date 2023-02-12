Il topological sort è un algoritmo utilizzato per ordinare i nodi di un [[Grafi|grafo]] diretto in modo che per ogni arco (u, v) del grafo, u viene prima di v nell'ordinamento. In altre parole, il topological sort garantisce che se un nodo dipende da un altro nodo, quest'ultimo verrà prima nell'ordinamento.

L'algoritmo di topological sort utilizza una tecnica di ordinamento in profondità ([[DFS]]) per visitare tutti i nodi del grafo e poi inserire i nodi nell'ordine inverso in cui sono stati visitati. In questo modo, i nodi che sono dipendenti da altri nodi verranno inseriti nell'ordinamento dopo i loro predecessori.

<img src=https://i.imgur.com/OqTn5p4.png width="120%" />
# Lemma 22.11

Un grafo orientato è aciclico se e soltanto se una visita in profondità ([[DFS]]) non genera archi all'interno 

## Dimostrazione

- Supponiamo che ci sia un arco all'indietro (u,v). Allora il vertice *v* è un antenato del vertice *u* della foresta DF. Quindi, esiste un cammino che va da *v* a *u* nel [[Grafi|grafo]] Ge l'arco indietro (u,v) completa un ciclo.

- Supponiamo che il grafo G contenga un ciclo 'c'. Dimostriamo che una visita in profondità di G genera un arco all'indietro. 
- Sia *v* il primo vertice che viene scoperto in 'c' e sia (u,v) l'arco precedente in 'c'. Al tempo *v.d*, i vertici di 'c' formano un cammino di vertici Bianchi da *v* a *u*. Per il teorema del cammino bianco, il vertice *u* diventa un discendente di *v* nella foresta DF. Dunque, (u,v) è un arco all'indietro.

# Teorema 22.12

TPOLOGICAL-SORT(G) produce un ordinamento topologico di un grafo orientato aciclico G

## Dimostrazione

Supponiamo che la procedura [[DFS]] venga eseguita su un dato dag      G = (V,E) per determinare i tempi di completamento dei suoi vertici. E' sufficiente dimostrare che per una coppia qualsiasi di vertici distinti *u*,*v* ∈ V, se ∃ un arco in G che va da *u* a *v*, allora *v.f* < *u.f*. Consideriamo un arco qualsiasi (u,v) ispezionato da [[DFS]](G). Quando questo arco viene ispezionato, il vertice *v* non può essere grigio, perchè altrimenti *v* sarebbe un antenato di *u* e (u,v) sarebbe un arco all'indietro, contraddicendo il Lemma 22.11. Quindi, il vertice *v* deve essere Bianco o Nero. Se *v* è bianco, diventa un discendente di *u* e quindi *v.f* < *u.f*. Se *v* è Nero, la sua ispezione è stata già completata, quindi il valore di *v.f* è stato già impostato. Poichè stiamo ancora ispezionando dal vertice *u*, dobbiamo ancora assegnare un'informazione temporale a *u.f* e, quando lo faremo, avremo ancora *v.f* < *u.f*. Quindi, per qualsiasi arco (u,v) nel dag, si ha *v.f* < *u.f*, e questo dimostra il teorema.
