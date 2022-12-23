
>Cammini minimi in grafi:
>cammiani minimi a singola sorgente (senza pesi negativi)

## Cammini minimi in grafi pesati

Sia G = (V, E, w) un grafo orientato o non orientato con pesi w reali sugli archi. Il costo o lunghezza di un cammino $\pi = <v_0,v_1,v_2,...,v_k>$ è:
$$w(\pi) = \sum_{i=1}^k w(v_{i-1}, v_i)$$
Un cammino minimo tra una coppia di vertici $x$ e $y$ è un cammino avente costo minore o uguale a quello di ogni altro cammino tra gli stessi vertici.

>[!note]- Nota:
>il cammino minimo non è necessariamente unico.

[Esempio: cammino minimo su un grafo pesato](http://www.mat.uniroma2.it/~guala/Dijkstra_2021.pdf#page=4)

![[immagine320.png]]
![[immagine321.png]]

>[!question]- Domanda:
>Esiste sempre un cammino fra due nodi?

... no!
- se non esiste nessun cammino da $u$ a $v$ 
	- $d(u, v)=+\infty$ 
- se c'è un cammino che contiene un ciclo il cui costo è negativo
	- $d(u,v)=-\infty$

![[immagine322.png]]

Sottostruttura ottima:
Ogni sottocammino di un cammino minimo è un cammino minimo.

![[immagine323.png]]

Disuguaglianza triangolare:
per ogni $u, v, x \in V$, vale:
	$d(u,v)\leq d(u,x)+d(x,v)$

![[immagine324.png]]
![[immagine325.png]]

## Problema del calcolo dei cammini minimi a singola sorgente

Due varianti:

- Dato G = (V, E, w), $s \in V$, calcola le distanze di tutti i nodi da $s$, ovvero, $d_G(s,v)$ per ogni $v\in V$
- Dato G = (V, E, w), $s\in V$, calcola l'albero dei cammini minimi di G radicato in $s$

## Albero dei cammini minimi (o Shortest Path Tree - SPT)

T è un albero dei cammini minimi con sorgente $s$ di un grafo G = (V, E, w) se:
- T è un albero radicato in $s$
- per ogni $v\in V$ vale:
	- $d_T(s, v) = d_G(s,v)$

![[immagine326.png]]
![[immagine327.png]]

>[!important]- Assunzione:
>Algoritmo di Dijkstra:
>Tutti gli archi hanno peso non negativo, ovvero ogni arco $(u,v)$ del grafo ha peso $w(u,v)\geq 0$

[Idea intuitiva dell'algoritmo: pompare acqua nella sorgente](http://www.mat.uniroma2.it/~guala/Dijkstra_2021.pdf#page=21)

## Verso l'algoritmo: approccio greedy (goloso)

1. Mantenere per ogni nodo $v$ una stima (per eccesso) $D_{sv}$ alla distanza $d(s,v)$. Inizialmente, unica stima finita $D_{ss}=0$.
2. Mantenere un insieme $X$ di nodi per cui le stime sono esatte; e anche un albero $T$ dei cammini minimi verso nodi in $X$ (albero nero). Inizialmente $X=\{s\}$, $T$ non ha archi.
3. Ad ogni passo aggiunge a $X$ il nodo $u$ in $V-X$ la cui stima è minima; aggiunge a $T$ uno specifico arco (arancione) entrante in $u$
4. Aggiorna le stime guardando i nodi adiacenti a $u$.

![[immagine328.png]]

I nodi da ggiungere progressivamente a $X$ (e quindi a $T$) sono mantenuti in una coda in priorità, associati ad un unico arco (arco arancione) che li connette a $T$.

La stima per un nodo $y \in V-X$ è $D_{sy}=min\{D_{sx}+w(x,y):(x,y) \in E, x\in X\}$.
L'arco che fornisce il minimo è l'arco arancione.

Se $y$ è in coda con arco $(x, y)$ associato, e se dopo aver aggiunto $u$ a T troviamo un arco $(u,y)$ tale che $D_{su}+w(u,y)<D_{sx}+w(x,y)$, allora rimpiazziamo $(x,y)$ con $(u,y),$ ed aggiorniamo $D_{sy}$

![[immagine329.png]]
![[immagine330.png]]

[Esempio pratico: Algoritmo di Dijkstra](http://www.mat.uniroma2.it/~guala/Dijkstra_2021.pdf#page=37)

## Correttezza:
### Estendere l'albero dei cammini minimi

>[!important]- Lemma di Dijkstra (1959):
>sia G = (V, E, w) (diretto o non diretto) con pesi non negativi, e sia $T$ un sottoalbero dell'albero dei cammini minimi radicato in $s$ che include $s$ ma non include tutti i vertici raggiungibili da $s$. Sia $(u, v)$ l'arco che minimizza la quantità $d(s,t)+w(t,z)$ per ogni $t \in T$ e $z \notin T$. Allora $(u,v)$ appartiene a un cammino minimo da $s$ a $v$ e $d(s,v)=d(s,u)+w(u,v)$.
>
>Dim: Supponiamo per assurdo che $(u,v)$ non appartenga ad un cammino da $s$ a $v,$ e quindi che $d(s,v)<d(s,u)+w(u,v)$.
>Allora, $d(s,v)$ è la lunghezza di un cammino minimo da $s$ a $v$ che non passa per $(u,v)$.

![[immagine331.png]]
![[immagine332.png]]

![[immagine333.png]]
![[immagine334.png]]

## Analisi della complessità

![[immagine335.png]]
![[immagine336.png]]
![[immagine337.png]]
![[immagine338.png]]
![[immagine339.png]]
