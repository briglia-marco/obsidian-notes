
* [x] Sintassi e grammatiche
	* [x] Definizione di [[Grammatica]]
	* [x] Definizione di [[Linguaggio]]
	* [x] Le fasi di un [[Compilatore]]
	* [x] [[BNF e sintassi]] di un linguaggio di programmazione
---
* [ ] Linguaggio L (vedi LinguaggioL-CheatSheet)
	* [x] [[BNF e Sintassi]]
	* [x] Regole semantica statica
		* [x] Espressioni
		* [x] Comandi
		* [x] Dichiarazioni 
		* [x] Funzioni: dichiarazione e chiamata
		* [ ] Funzioni ricorsive (dichiarazione e chiamata)
	* [x] Scoping e blocchi (identificatori liberi e legati)
	* [x] [[Record di attivazione]]
	* [ ] Regole semantica dinamica
		* [x] Espressioni
		* [x] Comandi
		* [x] Dichiarazioni
		* [ ] Funzioni: dichiarazione (lambda astrazione e chiusure) e chiamata
		* [ ] Funzioni ricorsive (dichiarazione e chiamata)
---
* [x] Complessità degli algoritmi
	* [x] Definizione formale di O, Ω, Θ, o, ω (vedi Cormen)
---
* [x] Algoritmi di ordinamento
	* [x] Ordinamento per confronti
		* [x] [[Insertion Sort|Insertion]] e [[Selection sort]]
			* [x] Dimostrazione di correttezza e complessità (vedi Cormen)
		* [x] [[Merge Sort]]
			* [x] Dimostrazione di correttezza e complessità (vedi Cormen)
		* [x] [[Quick Sort]] (vedi Cormen)
			* [x] Dimostrazione di correttezza
			* [x] Complessità al caso peggiore
			* [x] Dimostrazione complessità al caso medio
		* [x] Dimostrazione [[Lower bound Ω(n log n)]] problema di ordinamento per confronti
	* [x] Ordinamenti senza confronti (vedi Cormen e appunti)
		* [x] [[Counting sort]]
		* [x] [[Radix sort]]
---
* [x] [[Divide-et-impera]]: definizione e problemi
* [x] Il problema delle selezione: [[Selezione randomizzata]] (vedi Cormen)
* [ ] [[Equazioni di ricorrenza]] e loro risoluzione (vedi Cormen)
	* [x] Metodo iterativo
	* [x] Risoluzione mediante albero
	* [ ] [[Master Theorem]]
		* [x] Enunciato
		* [ ] Dimostrazione
---
* [x] Ricerca di un elemento in una collezione
	* [x] [[Ricerca lineare]] (progettazione algoritmo, correttezza, limite inferiore al problema e complessità della soluzione progettata)
	* [x] [[Ricerca binaria]] mediante divide-et-impera (progettazione algoritmo, correttezza e complessità)
---
* [x] [[Heap]] (vedi Cormen)
	* [x] Proprietà strutturale e sulle informazioni (di massimo e di minimo)
	* [x] Costruire uno heap (correttezza e complessità)
	* [x] Inserimento di un nodo e estrazione della radice
	* [x] Heapsort (correttezza e complessità)
---
* [x] [[Hash map|Tabelle e funzioni hash]] (vedi Cormen)
	* [x] Gestione collisioni
		* [x] Chaining (liste di trabocco)  
		* [x] Probing-Open hash (lineare, quadratico, doppio hash)
		* [x] Costi e complessità (dimostrazioni al caso medio, almeno l’idea intuitiva)
---
* [x] [[Alberi binari]]
	* [x] Definizione, e altezza nel caso peggiore e ottimo
	* [x] Visite: simmetrica, anticipata e posticipata
---
* [x] [[Albero di Ricerca Binario]] (vedi Cormen)
	* [x] Definizione, e altezza nel caso peggiore e ottimo
	* [x] Interrogazioni (ricerca, Min, Max, Successore, Predecessore) e operazioni di modifica (inserimento, cancellazione) e loro costi
---
* [x] [[2-3 Alberi]] (dispensa di Pino Italiano, su Classroom alla Lezione 46 - 2022)
	* [x] Definizione, e altezza nel caso peggiore e ottimo
	* [x] Operazioni di ricerca, inserimento e cancellazione e loro costi
---
* [x] [[Programmazione dinamica]]
	* [x] [[Longest Common Subsequence (LCS)]]
	* [x] [[Edit Distance]]
	* [x] [[Zaino]]
---
* [x] [[Greedy]] (zaino frazionario) 
---
* [x] [[Grafi]]
	* [x] [[BFS]] (vedi Cormen, con dimostrazione di: Lemma 22.1, 22.2,  e Teorema 22.5, almeno l’idea intuitiva)
	* [x] [[DFS]] (vedi Cormen, con dimostrazione dei  Teoremi 22.7, 22.8 e 22.10, almeno l’idea intuitiva)
	* [x] [[Topological sort]] (vedi Cormen, con dimostrazione del Lemma 22.11 e del Teorema 22.12)
	* [x] Cammini minimi (Dijkstra, Bellman-Ford - da appunti, no dimostrazioni)
---
* [x] [[P - NP]] (vedi appunti)
	* [x] Definizioni di P, NP, NP-arduo, NP-completo
	* [x] Esempio di riduzione [[3SAT]]