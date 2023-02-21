Il Master Theorem è un teorema delle [[Equazioni di ricorrenza]] che si applica a ricorrenze di forma:

![](https://i.imgur.com/GdkHs8i.png)

# Intuizione

$f(n)$ vs $n^{log_ba}$ 

> Il più grande asintoticamente determina il risultato

# 1° Caso

Se $f(n) = O(n^{log_ba-\varepsilon})$ per qualche costante $\varepsilon > 0$:
- quindi $f(n)$ cresce polinomialmente più lentamente di $n^{log_ba}$ (di un fattore $n^\varepsilon$) ==> $f(n) < n^{log_ba}$

### Soluzione

> $T(n) = \theta(n^{log_ba})$ 


# 2° Caso

Se $f(n) = \Theta(n^{log_ba}lg^{k}n)$ per qualche costante k>=0:
- quindi $f(n)$ e $n^{log_ba}$ crescono allo stesso modo

### Soluzione

> $T(n) = \Theta(n^{log_ba}lg^{k+1}n)$ 


# 3° Caso

Se $f(n) = \Omega(n^{log_ba+\varepsilon})$ per qualche costanate $\varepsilon > 0$:
- Quindi $f(n)$ cresce polinomialmente più veloce di $n^{log_ba}$ (di un fattore $n^\varepsilon$) ==> $f(n) > n^{log_ba}$ **e**
- $f(n)$ soddisfa la *condizione* che:
	- $af(n/b) <= cf(n)$ per qualche costante $c<1$ e $n>n_0$ 

### Soluzione

> $T(n) = \Theta(f(n))$ 