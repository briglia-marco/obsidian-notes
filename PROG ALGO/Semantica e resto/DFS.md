Dato G=(V,E) e un vertice S (sorgente) ispeziona tutti gli archi per trovare tutti i vertici raggiungibili da S.
A differenza della [[BFS]] utilizza una [[pila]] anzichè un [[lista]].

> *Bianco* => Nodo non ancora scoperto
> *Grigio* => Visitato ma non analizzato
> *Nero* => Esaurito (tolto dalla [[pila]])

- Parto da S e "grigio" il suo diretto successore => S -> Nero;
- Il successore va in una pila P;
- Seguo P fino ad aver esaurito tutti i nodi.

# Teorema 22.7

3 casi:
- [u.d, u.f] e [v.d, v.f] sono completamenti disgiunti => non sono discendenti l'uno dell'altro
- [u.d, u.f] è interamente contenuto in [v.d, v.f] => *u* è discendente di *v*
- [v.d, v.f] è interamente contenuto in [u.d, u.f] => *v* è discendente di *u*

# Corollario 22.8

*v* è discendente di *u* <=> u.d<v.d<v.f<u.f