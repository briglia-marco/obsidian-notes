La riduzione 3SAT è una tecnica utilizzata per trasformare un problema di satisifiability di una formula logica in un problema di satisfiability di un'altra formula logica. La riduzione 3SAT consente di risolvere problemi complessi utilizzando algoritmi più semplici, come ad esempio l'algoritmo di satisifiability 2SAT.

Questo è un esempio di riduzione 3SAT:

Supponiamo di avere una formula logica che consiste di tre proposizioni: `A`, `B` e `C`. La formula logica può essere rappresentata come segue:

```
(A or B or C) and (not A or B or not C) and (A or not B or not C)
```

Per risolvere questo problema tramite la riduzione 3SAT, possiamo trasformare la formula logica in un grafo bipartito. Ogni proposizione viene rappresentata da un nodo nel grafo e le relazioni tra le proposizioni vengono rappresentate da archi tra i nodi.

In questo esempio, possiamo trasformare la formula logica in tre nodi: un nodo per ogni proposizione. Ogni nodo avrà due archi che rappresentano le due possibili valutazioni della proposizione (vero o falso). Se una proposizione viene valutata come vera, l'arco che rappresenta questa valutazione verrà seguito. Se una proposizione viene valutata come falsa, l'arco che rappresenta questa valutazione verrà ignorato.

Infine, possiamo risolvere il problema tramite l'algoritmo 2SAT. L'algoritmo 2SAT consiste nell'esaminare ogni nodo e nell'assegnare un valore di vero o falso in modo che la formula logica sia soddisfacente.

In questo esempio, l'algoritmo 2SAT garantirà che la formula logica sia soddisfacente seguendo uno dei due archi per ogni nodo. La soluzione finale dipenderà dalla scelta degli archi che vengono seguiti.

# Esempio

Supponiamo di avere la seguente istanza di 3SAT:

$(x_1 \lor \neg x_2 \lor x_3) \land (\neg x_1 \lor x_2 \lor \neg x_3) \land (\neg x_1 \lor \neg x_2 \lor x_3)$

Per ridurre questa istanza di 3SAT ad un'istanza di problema di soddisfacibilità booleana (SAT), possiamo usare la seguente tecnica:

Per ogni clausola $(x_i \lor x_j \lor x_k)$, dove $x_i$, $x_j$ e $x_k$ sono letterali, creiamo una nuova variabile $y_c$ e le due clausole:

$(\neg x_i \lor \neg x_j \lor y_c)$

$(\neg y_c \lor x_i)$, $(\neg y_c \lor x_j)$, $(\neg y_c \lor x_k)$

In questo modo, la clausola $(x_i \lor x_j \lor x_k)$ è equivalente alla clausola $(\neg x_i \lor \neg x_j \lor y_c)$ se e solo se $y_c$ è vero, e le clausole $(\neg y_c \lor x_i)$, $(\neg y_c \lor x_j)$, $(\neg y_c \lor x_k)$ sono soddisfatte.

Applicando questa tecnica all'istanza di 3SAT iniziale, otteniamo le seguenti clausole:

$(\neg x_1 \lor \neg x_2 \lor y_1)$, $(\neg y_1 \lor x_1)$, $(\neg y_1 \lor x_2)$, $(\neg y_1 \lor x_3)$

$(\neg x_1 \lor x_2 \lor \neg y_2)$, $(\neg y_2 \lor x_1)$, $(\neg y_2 \lor \neg x_2)$, $(\neg y_2 \lor x_3)$

$(\neg x_1 \lor \neg x_2 \lor y_3)$, $(\neg y_3 \lor x_1)$, $(\neg y_3 \lor x_2)$, $(\neg y_3 \lor x_3)$

Ora possiamo risolvere l'istanza di SAT utilizzando un algoritmo di soddisfacibilità booleana come ad esempio l'algoritmo DPLL.
