> Vogliamo definire la distanza fra 2 stringhe con la [[Programmazione dinamica]]

# Definizione

La distanza fra 2 stringhe è il numero minimo di operazioni che devo fare per strasformare la prima stringa nella seconda, dove le operazioni che posso fare sono:
 - *Copiare*: un carattere da `x` a `z`, impostando `z[j]` = `x[i]` e poi incrementando i e j. Questa operazione esamina `x[i]`.
 - *Sostituire*: un carattere di `x` con un altro  carattere `c`, impostando `z[j]` = `c` e poi incrementando i e j. Questa operazione esamina `x[i]`.
 - *Cancellare*: un carattere di `x`, incrementando i, senza modificare j. Questa operazione esamina `x[i]`.
 - *Inserire*: il carattere `c` in `z`, impostando `z[j]` = `c` e poi incrementando j. Questa operazioni non esamina i caratteri di x.
 - *Scambiare*: i prossimi 2 caratteri copiandoli da `x` a `z`, ma in ordine inverso; per fare questo, impostiamo prima `z[j] = x[i+1]` e `z[j+1] = x[i]` e, poi, `i = i+2` e     `j = j+2`. Questa operazione esamina `x[i]` e `x[i+1]`.
 - *Distruggere*: la parte restante di `x`, impostando `i = m+1`. Questa operazione esamina tutti i caratteri di `x` che non sono ancora stati esaminati. Se questa operazione viene svolta, deve essere l'ultima.

![](https://i.imgur.com/yBOOrEk.png)

Con l'allineamento posso andare vedere velocemente le differenze e le uguaglianze fra le `stringhe` che sto confrontando.
In questo esempio noto che ho bisogno di 4 operazioni per trasformare `presto` in `risotto`, 1 *cancellazione* e 3 *sostituzioni/copie*.

> Ogni spazio o carttere di `x` deve corrispondere al corrispondente della stringa `y`. 

# Algoritmo

## Calcolo Distanza

```js
function editDistance(str1, str2) {
  const m = str1.length; // lunghezza della prima stringa
  const n = str2.length; // lunghezza della seconda stringa
  
  // inizializzazione della matrice delle distanze
  const dp = new Array(m+1).fill().map(() => new Array(n+1).fill(0));
  // dp[i][j] contiene la distanza tra i primi i caratteri di str1 e i primi j caratteri di str2
  
  // riempimento della prima riga e colonna della matrice
  for (let i = 0; i <= m; i++) {
    dp[i][0] = i; // distanza tra una sottostringa vuota e una di lunghezza i
  }
  for (let j = 0; j <= n; j++) {
    dp[0][j] = j; // distanza tra una sottostringa di lunghezza j e una vuota
  }
  
  // calcolo delle distanze
  for (let i = 1; i <= m; i++) {
    for (let j = 1; j <= n; j++) {
      if (str1[i-1] === str2[j-1]) { // se i caratteri corrispondenti sono uguali
        dp[i][j] = dp[i-1][j-1]; // la distanza non cambia rispetto alla sottostringa precedente
      } else {
        dp[i][j] = 1 + Math.min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]);
        // altrimenti, aggiungi un costo di 1 per l'operazione di inserimento, cancellazione o sostituzione
        // che porta alla sottostringa corrente con i caratteri corrispondenti uguali
        // e scegli il minimo tra le tre opzioni
      }
    }
  }
  
  // restituzione della distanza tra le due stringhe
  return dp[m][n];
}
```

>  - L'algoritmo utilizza una matrice `dp` di dimensioni `(m+1)x(n+1)` per calcolare la distanza tra le due stringhe `str1` e `str2`, dove `m` e `n` sono le lunghezze delle stringhe. La cella `dp[i][j]` contiene la distanza tra i primi `i` caratteri di `str1` e i primi `j` caratteri di `str2`.
 > - L'algoritmo riempie la prima riga e colonna della matrice `dp` con le distanze tra le sottostringhe vuote e le sottostringhe di lunghezza `i` e `j` rispettivamente. Successivamente, calcola la distanza tra ogni coppia di prefissi delle due stringhe. Se i caratteri corrispondenti in entrambe le stringhe sono uguali, la distanza tra le due sottostringhe non cambia rispetto alla sottostringa precedente, altrimenti viene aggiunto un costo di 1 per l'operazione di inserimento, cancellazione o sostituzione necessaria per far corrispondere i due caratteri.
>  - Alla fine, la funzione restituisce la distanza tra le due stringhe, contenuta nell'ultima cella della matrice `dp`.

## Allineamento (sapere in generale)

```js
function allineamento(seq1, seq2, match = 2, mismatch = -1, gap = -2) {
  const m = seq1.length;
  const n = seq2.length;

  // inizializzazione della matrice delle punteggi
  const scores = new Array(m+1).fill().map(() => new Array(n+1).fill(0));

  // riempimento della prima riga e colonna della matrice dei punteggi con i punteggi relativi all'apertura di gap
  for (let i = 1; i <= m; i++) {
    scores[i][0] = gap * i;
  }
  for (let j = 1; j <= n; j++) {
    scores[0][j] = gap * j;
  }

  // calcolo dei punteggi per tutte le celle della matrice
  for (let i = 1; i <= m; i++) {
    for (let j = 1; j <= n; j++) {
      const matchScore = scores[i-1][j-1] + (seq1[i-1] === seq2[j-1] ? match : mismatch); // punteggio dell'allineamento in cui seq1[i-1] e seq2[j-1] sono allineati
      const deleteScore = scores[i-1][j] + gap; // punteggio dell'allineamento in cui seq1[i-1] è allineato con un gap
      const insertScore = scores[i][j-1] + gap; // punteggio dell'allineamento in cui seq2[j-1] è allineato con un gap
      scores[i][j] = Math.max(matchScore, deleteScore, insertScore); // punteggio massimo tra i tre possibili allineamenti
    }
  }

  // ricostruzione dell'allineamento a partire dalla matrice dei punteggi
  let align1 = '';
  let align2 = '';
  let i = m;
  let j = n;
  while (i > 0 || j > 0) {
    if (i > 0 && j > 0 && scores[i][j] === scores[i-1][j-1] + (seq1[i-1] === seq2[j-1] ? match : mismatch)) {
      align1 = seq1[i-1] + align1; // il carattere in posizione i-1 di seq1 è allineato
      align2 = seq2[j-1] + align2; // il carattere in posizione j-1 di seq2 è allineato
      i--;
      j--;
    } else if (i > 0 && scores[i][j] === scores[i-1][j] + gap) {
      align1 = seq1[i-1] + align1; // il carattere in posizione i-1 di seq1 è allineato con un gap
      align2 = '-' + align2; // la posizione j-1 di seq2 è occupata da un gap
      i--;
    } else {
      align1 = '-' + align1; // la posizione i-1 di seq1 è occupata da un gap
      align2 = seq2[j-1] + align2; // il carattere in posizione j-1 di seq2 è allineato con un gap
      j--;
    }
  }

  return [align1, align2];
}

```

> La funzione `allineamento` prende in input due sequenze `seq1` e `seq2`, e tre valori opzionali: `match` (punteggio per il matching di due caratteri uguali), `mismatch` (punteggio per la non corrispondenza di due caratteri diversi) e `gap` (punteggio per l'apertura di una posizione vuota nell'allineamento).

# Complessità

La complessità di ricerca della Edit Distance con l'algoritmo di [[Programmazione dinamica]] è di O(nm).

