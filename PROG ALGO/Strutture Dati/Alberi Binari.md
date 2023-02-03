<img src=https://i.imgur.com/th9XaIb.png width="60%" />

# Caratteristiche

E' una struttura definita su un insieme di nodi che:
-   Non contiene alcun nodo (albero vuoto)
-   Contiene un nodo detto radice, un sottoalbero sinistro e un sottoalbero destro (entrambe binari)

## Definizioni

Con esempio l’albero sopra:
-   Dimensione Albero
	-    # Nodi albero  ⇒ 9   

-   Altezza Albero
	-   Massima distanza foglia/radice ⇒ 3

-   Altezza nodo
	-   Massima distanza nodo/radice ⇒ altezza nodo 5 = 2

-   Profondità nodo 
	-   Distanza nodo/radice ⇒ profondità nodo 5 = 1


# Pro e Contro

Pro:

-   Efficienti per la ricerca: gli alberi binari sono efficienti per la ricerca di elementi specifici all'interno della struttura. La ricerca in un albero binario richiede un tempo medio O(log n) in base al numero di elementi nell'albero.
-   Facili da capire e implementare
-   Utilizzabili in molti algoritmi: gli alberi binari sono utilizzati in molti algoritmi, come quelli di ordinamento e ricerca, rendendoli una struttura dati molto versatile.

Contro:

-   Non sono efficienti per la modifica: le operazioni di inserimento, eliminazione e modifica degli elementi possono essere più complesse e meno efficienti rispetto ad altre strutture dati    
-   Occupano più spazio: gli alberi binari richiedono più spazio di altre strutture dati come le liste o gli array, poiché ogni elemento ha uno o due puntatori ad altri elementi.
-   Non sono sempre adatti a tutti i casi d'uso: gli alberi binari potrebbero non essere la scelta migliore per alcuni problemi di dati, come quelli che richiedono una grande quantità di modifiche frequenti o una grande quantità di dati non ordinati.

# Algoritmi

## 1) Visita Anticipata (pre visita)

La visita di una nodo precede la visita dei suoi sottoalberi:

```js
if(u != null){
	*esamina u*
	anticipata(u.left)
	anticipata(u.right)
}
```

## 2) Visita Simmetrica (in visita)

La visita di un nodo è intermediata alla visita ricorsiva dei suoi sottoalberi:

```js
**

if(u != null){
	simmetrica(u.left)
	*esamina u*
	simmetrica(u.right)
}
```

## 3) Visita Posticipata (post visita)

```js
if(u != null){
posticipata(u.left)
posticipata(u.right)
*esamina u*
}
```

# Complessità

- Caso Ottimo
	- O(log  n)

- Caso Medio
	- O(log n)

- Caso Pessimo
	- O(n)

