## Sottosequenza

Data una sequenza X = <x1, x2, x3, ..., xm>, un'altra sequenza  Z = <z1, z2, z3, ..., zk> è una *sottosequenza* di X se ∃ una sequenza strettamente crescente <i1, i2, i3, ..., ik> di indici di X tale che ∀j = 1,2,...,k, si ha `x[ij]` = `z[j]`.

> EX. 
> Z = <**B,C,D,B**> è una sottosequenza di X = <A,**B,C**,B,**D**,A,**B**> 
> con corrispondenza di indici <**2,3,5,7**>

* ### Sottoseuquenza comune

Date 2 sequenze, X = <A,B,C,B,D,A,B> e Y = <B,D,C,A,B,A>, allora 
Z = <B,C,A> è una sottosequenza comune, ma non è la sottosequenza comune più lunga (LCS).
Infatti LCS possono essere <B,C,B,A> oppure <B,D,A,B> che hanno dimensione 4 perchè non esistono LCS di dimensione 5.

## Calcolare la più lunga sottosequenza comune (LCS)

### Fase 1: Caratterizzare la più lunga sequenza comune

Il problema della LCS gode della proprietà della [[Sottostruttura ottima]], come dimostra il teorema a seguire. Le classi naturali di sottoproblemi corrispondono a coppie di "prefissi" della due sequenza in input.

> EX. 
> X = <x1,x2,x3,...,xm>;
> i = i-esimo prefisso di X;
> se X = <A,B,C,D,B,D> ==> X4 = <A,B,C,D> | X0 = ∅ | X2 = <A,B>

#### Teorema 15.1

Siano X = <x1,x2,x3,...,xm> e Y = <y1,y2,y3,...,yn> le sequenze;
sia Z = <z1, z2, z3, ..., zk> una qualsiasi LCS di X e Y

1) se xm = yn ==> zk = xm e Zk-1 è una LCS di Xm-1 e Yn-1
2) se xm != yn ==> zk != xm e Z è una LCS di Xm-1 e Y
3) se xm != yn ==> zk != yn e Z è una LCS di X e Yn-1

> La caratterizazione del Teorema 15.1 dimostra che una LCS di due sequenze contiene al suo interno una LCS di prefissi delle due sequenze. Quindi il problema della più lunga sottosequenza comune gode della proprietà della [[Sottostruttura ottima]] 

### Fase 2: Soluzione ricorsiva

Definiamo c[i,j] come lunghezza di una LCS delle sequenze Xi e Yj. Se i = 0 o j = 0, una delle sequenze ha lunghezza 0, quindi la LCS ha lunghezza 0. La [[Sottostruttura ottima]] del problema della LCS consente di di scrivere la formula ricorsiva:

> 		  {0                       ==> se i =0 o j = 0
> c[i,j] =  {c[i-1,j-1]+1            ==> se i,j > 0 e xi = yj
> 		  {max(c[i,j-1],c[i-1,j])  ==> se i,j > 0 e xi != yj

### Fase 3: Calcolare la lunghezza di una LCS

Con l'equzione scritta sopra creiamo un metodo che risolve il problema in tempo esponenziale. Non buono siccome abbiamo solo O(mn) sottoproblemi distinti. possiamo utilizzare la programmazione dinamica per calcolare le soluzione con metodo bottom-up. 

#### Algoritmo

```js
function lcsLength(X, Y) {
  const m = X.length;
  const n = Y.length;
  const dp = []; // Matrice di programmazione dinamica

  // Inizializza la matrice con 0 in tutte le celle
  for (let i = 0; i <= m; i++) {
    dp[i] = Array(n + 1).fill(0);
  }

  // Riempie la matrice con i valori corretti
  for (let i = 1; i <= m; i++) {
    for (let j = 1; j <= n; j++) {
      if (X[i - 1] === Y[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + 1;
      } else {
        dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
      }
    }
  }

  // L'elemento in posizione (m, n) contiene la lunghezza della LCS
  return dp[m][n];
}
```

> In questo metodo, la soluzione viene costruita partendo dai sotto-problemi di dimensione minore e risolvendoli iterativamente in un ciclo for, fino a raggiungere la soluzione del problema originale.
> L'idea di base dell'algoritmo bottom-up è simile all'algoritmo top-down con memoization: si costruisce una matrice di programmazione dinamica per archiviare i risultati dei sotto-problemi già risolti e utilizzare questi risultati per risolvere il problema originale.
  Nel codice, la matrice `dp` viene inizializzata con tutti gli elementi a 0. Poi, vengono utilizzati due cicli for per calcolare il valore di ogni cella della matrice `dp` a partire dai sotto-problemi di dimensione minore. La cella `(i, j)` contiene la lunghezza della LCS tra i primi i caratteri di `X` e i primi j caratteri di `Y`.
  Infine, l'elemento in posizione `(m, n)` della matrice `dp` contiene la lunghezza della LCS tra le due stringhe `X` e `Y`.

Il tempo di esecuzione della procedura è O(mn) perchè il calcolo di ogni posizione nella tabella richede 1.

### Fase 4: Costruire una LCS

Con la tabella `b` restituita da `LCS-Length` possiamo costruire rapidamente una LCS delle sequenze X e Y. 

```js
function printLcs(b, X, i, j) {
  if (i === 0 || j === 0) {
    return '';
  }

  if (b[i][j] === 'diagonal') {
    // Se l'elemento in posizione (i, j) è stato ottenuto dall'elemento in
    // posizione (i-1, j-1), allora è un carattere comune ad entrambe le
    // stringhe e deve essere incluso nella LCS
    return printLcs(b, X, i - 1, j - 1) + X[i - 1];
  } else if (b[i][j] === 'up') {
    // Se l'elemento in posizione (i, j) è stato ottenuto dall'elemento in
    // posizione (i-1, j), allora è un carattere che compare solo nella
    // stringa X e non deve essere incluso nella LCS
    return printLcs(b, X, i - 1, j);
  } else {
    // Altrimenti, l'elemento in posizione (i, j) è stato ottenuto
    // dall'elemento in posizione (i, j-1), e deve essere ignorato nella LCS
    return printLcs(b, X, i, j - 1);
  }
}
```

  * Questa funzione utilizza la matrice `b` generata dall'algoritmo LCS per ricostruire una delle possibili LCS tra le stringhe `X` e `Y` a partire dalla posizione `(i, j)`.

  * La funzione utilizza una logica ricorsiva per esplorare la matrice `b` partendo dalla posizione `(i, j)` e risalendo la matrice lungo una delle tre possibili direzioni: a sinistra, in alto, o diagonalmente in alto a sinistra.

  * Se l'elemento in posizione `(i, j)` è stato ottenuto dall'elemento in posizione `(i-1, j-1)`, allora il carattere `X[i-1]` è un carattere comune ad entrambe le stringhe e deve essere incluso nella LCS.

  * Se l'elemento in posizione `(i, j)` è stato ottenuto dall'elemento in posizione `(i-1, j)`, allora il carattere `X[i-1]` compare solo nella stringa `X` e non deve essere incluso nella LCS.

  * Se l'elemento in posizione `(i, j)` è stato ottenuto dall'elemento in posizione `(i, j-1)`, allora il carattere `Y[j-1]` compare solo nella stringa `Y` e non deve essere incluso nella LCS.

  * La funzione restituisce una stringa che rappresenta la LCS tra `X` e `Y` a partire dalla posizione `(i, j)`.
