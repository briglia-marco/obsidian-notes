
<img src=https://i.imgur.com/9pGnuXH.png width="80%"/>

# Caratteristiche

Una hash map (nota anche come tabella hash) è una struttura di dati che associa chiavi a valori, permettendo di cercare, inserire e rimuovere elementi in modo efficiente. Le seguenti sono alcune delle caratteristiche più importanti di una hash map:
 
1.  Mapping chiave-valore: Una hash map associa una chiave a un valore, permettendo di accedere al valore corrispondente a una chiave specifica in modo rapido.

2.  Hash function: Una hash map utilizza una funzione hash per mappare le chiavi a indici di array. La funzione hash deve essere efficiente e distribuire uniformemente le chiavi nello spazio di indirizzi.

3.  Collisioni: Può verificarsi una collisione quando più chiavi mappano allo stesso indice di array. Una hash map deve gestire le collisioni in modo efficiente, ad esempio tramite l'utilizzo di una lista di trabocco o una mappa di trabocco.

4.  Tempo di accesso O(1): In media, una hash map permette di accedere a un valore in tempo costante O(1), indipendentemente dal numero di elementi nella mappa.

5.  Non ordinato: Le hash map non garantiscono un ordine specifico per le coppie chiave-valore.

6.  Non ordinabile: Le hash map non possono essere ordinate in modo nativo. Se è necessario ordinare i valori, è necessario convertire la hash map in un altro tipo di struttura dati ordinabile, ad esempio un array o una lista.

# Pro e Contro

Pro:

1.  Tempo di accesso rapido: Una delle caratteristiche più importanti di una hash map è il tempo di accesso rapido, che in media è di O(1). Questo rende le hash map adatte per molte applicazioni che richiedono una rapida ricerca di elementi.
2.  Uso efficiente della memoria: Le hash map utilizzano una funzione hash per mappare le chiavi a indici di array, il che consente di utilizzare la memoria in modo efficiente.
3.  Facilità di implementazione: Le hash map sono relativamente semplici da implementare rispetto ad altre strutture dati come le alberi binari di ricerca.

Contro:

1.  Collisioni: Uno svantaggio di una hash map è che le collisioni possono verificarsi quando più chiavi mappano allo stesso indice di array. Questo può ridurre l'efficienza della ricerca e dell'inserimento di elementi.
2.  Ordinamento non garantito: Le hash map non garantiscono un ordine specifico per le coppie chiave-valore, il che può rendere difficile lavorare con dati che richiedono un ordine specifico.
3.  Non adatto a tutti i casi d'uso: Le hash map possono essere meno efficienti per alcuni casi d'uso, ad esempio quando è necessario ordinare i valori o quando è necessario accedere ai valori in ordine. In questi casi, potrebbe essere più appropriato utilizzare una struttura dati diversa, come un array o una lista ordinata.

# Metodi di Hashing

## Liste di Trabocco

Le [[Liste]] di trabocco sono una soluzione per gestire le collisioni nella creazione di una tabella hash. Queste liste vengono utilizzate quando più chiavi hanno lo stesso valore hash e vengono memorizzate nella stessa posizione nella tabella hash.

Invece di risolvere la collisione cercando un'altra posizione nella tabella hash come nel caso di hashing lineare o quadratico, le liste di trabocco creano una lista di elementi che condividono lo stesso valore hash e li inseriscono in questa lista. Questa lista viene quindi percorsa per trovare la chiave desiderata.

Le liste di trabocco sono una soluzione semplice e conveniente per gestire le collisioni, ma possono aumentare la complessità del tempo di ricerca a causa del tempo necessario per scorrere la lista. Pertanto, è importante scegliere una buona funzione hash che distribuisca uniformemente le chiavi nella tabella hash per ridurre il numero di collisioni.

## Hashing Lineare

In questa tecnica, in caso di collisione, viene utilizzata un'altra posizione nella tabella hash, che viene calcolata come `(hash(k) + i) % m`, dove i è un intero che aumenta di uno ad ogni collisione partendo da i = 0.

## Hashing Quadratico

In questa tecnica, in caso di collisione, viene utilizzata un'altra posizione nella tabella hash, che viene calcolata come `(hash(k) + c1 * i + c2 * i^2) % m`, dove i è un intero che aumenta di uno ad ogni collisione e c1 e c2 sono costanti.

## Hasing Doppio

In questa tecnica, vengono utilizzate due funzioni hash diverse per calcolare l'indice di array per ogni chiave. In caso di collisione, si utilizza la seconda funzione hash per calcolare una nuova posizione nella tabella hash. Questa tecnica è spesso più efficiente rispetto alle tecniche di hashing lineare e quadratico.

>**Ex.**
>h(k, i) = (h1(k) + i*h2(k)) % m
>h1(k) = k % m
>h2(k) = 1 + k % m-1