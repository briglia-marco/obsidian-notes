Dato G=(V, E) e un vertice S (sorgente) ispeziona tutti gli archi per trovare tutti i vertici raggiungibili da S.
A differenza della [[DFS]] utilizza una [[Lista]] anzichè un [[Pila]].

> *Bianco* => Nodo non ancora scoperto
> *Grigio* => Visitato ma non analizzato
> *Nero* => Esaurito (tolto dalla [[Lista]])

- Parto da S e "grigio" tutti i suoi vicini => S -> Nero;
- I Grigi vanno in una coda Q;
- Seguo Q fino ad aver esaurito tutti i nodi.

# Lemma 22.1

- ∀ (u, v) ∈ E
- δ(s, v) <= δ(s, u) +1

![](https://i.imgur.com/hkTI3Mt.png)

# Lemma 22.2

v.d >= δ(s, v)
induzione con 22.1
v.d = u.d +1 = δ(s, u) + 1 = δ(s, v)

# Teorema 22.5

∀ v ∈ V raggiungibili da S:
- v.d = δ(s, v)
∀ v != s;
- Uno dei cammini minimi da S a *v* è un cammino minimo da s a v.π (predecessore) + l'arco (v.π, v)