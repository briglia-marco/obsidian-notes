
![](https://i.imgur.com/CIUQyjH.png)


# Caratteristiche

La coda ('queue' in inglese) **FIFO (First-In, First-Out)** è un tipo di coda in cui gli elementi vengono inseriti alla fine e estratti dall'inizio. Questo significa che l'elemento che è stato inserito per primo verrà elaborato per primo, seguito dall'elemento successivo, e così via. La coda FIFO è una struttura dati molto comune e viene utilizzata in molte applicazioni, come ad esempio la gestione delle operazioni di stampa, la gestione delle code di un supermercato o la gestione dei messaggi in un sistema di messaggistica.

Le caratteristiche principali di una coda FIFO sono:

1.  Ordine di inserimento: 
	- Gli elementi vengono inseriti in fondo alla coda e estratti dalla parte anteriore.

2.  Estrazione dell'elemento più vecchio: 
	- L'elemento più vecchio nella coda è quello che è stato inserito per primo e verrà elaborato per primo.

3.  Dimensione fissa o dinamica: 
	- Una coda può avere una dimensione fissa o dinamica, a seconda delle esigenze dell'applicazione.

4.  Accesso limitato: 
	- L'accesso alla coda è limitato alla sola parte anteriore, il che significa che gli elementi possono essere estratti solo dalla parte anteriore e inseriti solo in fondo.

5.  Concorrenza: 
	- Le code possono essere utilizzate in ambienti concorrenti, in cui più [[thread]] possono accedere alla coda contemporaneamente. Questo richiede una gestione adeguata della concorrenza per evitare conflitti tra thread.

6.  Modelli di accesso: 
	- Le code possono essere configurate per supportare diversi modelli di accesso, come ad esempio l'accesso in sola lettura o l'accesso in sola scrittura.

>In JS non esiste una struttura Coda, quindi o crei una classe o utilizzi metodi degli array per gestirlo come una coda

# Metodi

```js
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(element) {
    this.items.push(element);
  }

  dequeue() {
    return this.items.shift();
  }

  peek() {
    return this.items[0];
  }

  isEmpty() {
    return this.items.length === 0;
  }
}
```