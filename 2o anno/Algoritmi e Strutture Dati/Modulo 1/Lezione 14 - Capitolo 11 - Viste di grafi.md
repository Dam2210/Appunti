## Grafi non diretti

![[immagine285.png]]
![[immagine286.png]]
![[immagine287.png]]
![[immagine288.png]]

>[!note]- Nota
>Quali parti del grafo sono raggiungibili da un certo nodo?
>eseguo una vista del grafo

## Scopo e tipi di visita

- Una visita di un grafo G permette di esaminare i nodi e gli archi di G in modo sistematico (se G è connesso)
- Genera un albero di visita
- Problema di base in molte applicazioni
- Esistono vari tipi di visite con diverse priorità:
	- visita in ampiezza (BFS = breadth first search)
	- visita in profondità (DFS = depth first search)

## Visita in ampiezza

>dato un grafo G (non pesato) e un nodo s, trova tutte le distanze/cammini minimi da s verso ogni altro nodo v.

## Applicazioni

- Web crawling
	- come google trova nuove pagine da indicizzare
- Social networking
	- trovare gli amici che potresti conoscere
- Network broadcast
	- un nodo manda un messaggio a tutti gli altri nodi della rete
- Garbage collection
	- come scoprire memoria non più raggiungibile che si può liberare
- Model checking
	- verificare una proprietà di un sistema
- Risolvere puzzle
	- risolvere il Cubo di Rubik con un numero minimo di mosse

## Cubo di Rubik: 2x2x2

- Grafo delle configrazioni
	- un vertice per ogni possibile stato del cubo
	- un arco fra due configurazioni se l'una è ottenibile dall'altra tramite una mossa

![[immagine289.png]]
![[immagine290.png]]
![[immagine291.png]]

[Esempio: Visita BFS](http://www.mat.uniroma2.it/~guala/visite_2021.pdf#page=15)

![[immagine292.png]]
![[immagine293.png]]
![[immagine294.png]]

## Costo della visita in ampiezza

Il tempo di esecuzione dipende dalla struttura dati uasata per rappresentare il grafo (e dalla connettività o meno del grafo rispetto ad s):
- Liste di adiacenza: $O(m+n)$
- Matrice di adiacenza: $O(n^2)$ 

>[!note]- Osservazioni
>1. Si noti che se il grafo è connesso allora $m\geq n-1$ e quindi $O(m+n)=O(m)$
>2. Ricordando che $m\leq \frac{n(n-1)}{2}$, si ha $O(m+n)=O(n^2)$ 
>$\rightarrow$ per $m=o(n^2)$ la rappresentazione mediante liste di adiacenza è temporalmente più efficiente.

## Proprietà dell'albero BFS radicato in s

![[immagine295.png]]

- Se il grafo è non orientato, per ogni arco $(u, v)$ del grafo gli estremi $u$ e $v$ appartengono allo stesso livello o a livelli consecutivi dell'albero BFS.

![[immagine296.png]]

- Se il grafo è orientato, allora gli archi orientati verso il basso uniscono nodi sullo stesso livello o su livelli adiacenti, mentre gli archi orientati verso l'alto possono unire nodi su livelli non adiacenti.

>[!important]- Teorema
>Per ogni nodo $v$, il livello di $v$ nell'albero BFS è pari alla distanza di $v$ dalla sorgente $s$ (sia per grafi orientati che non orientati).

## Dimostrazione informale

- All'inizio inserisco $s$ in $F$ (che è a distanza $0$ da se stesso) e gli assegno livello $0$; chiaramente $s$ è l'unico nodo a distanza $0$.
- Estraggo $s$ e guardo tutti i suoi vicini (archi uscenti); questi sono tutti i nodi a distanza 1 da $s$; li inserisco in $F$ e assegno loro livello 1. Ora in $F$ ho tutti i nodi a distanza 1.
- Estraggo uno a uno tutti i nodi di livello/distanza 1 e per ogniuno guardo tutti i suoi vicini (archi uscenti); i vicini non marcati sono a distanza 2 da $s$; li inserisco in $F$ e assegno loro livello 2; quando ho estratto e visitato tutti i nodi di livello 1, in $F$ ho tutti i nodi a distanza 2 da $s$.
- Estraggo uno a uno tutti i nodi di livello/distanza 2 e per ogniuno guardo tutti i suoi vicini (archi uscenti); i vicini non marcati sono a diatanza 3 da $s$...

![[immagine297.png]]
![[immagine298.png]]

[Esempio: Visita DFS](http://www.mat.uniroma2.it/~guala/visite_2021.pdf#page=43)

![[immagine299.png]]
![[immagine300.png]]

## Costo della visita in profondità

Il tempo di esecuzione dipende dalla struttura dati usata per rappresentare il grafo (e dalla connettività o meno del grafo rispetto ad $s$):
- Liste di adiacenza: $O(m+n)$
- Matrice di adiacenza: $O(n^2)$

## Proprietà dell'albero DFS radicato in $s$

- Se il grafo è non orientato, per ogni arco $(u, v)$ si ha:
	- $(u, v)$ è un arco dell'albero DFS, oppure 
	- i nodi $u$ e $v$ sono l'uno discendente/antenato dell'altro
- Se il grafo è orientato, per ogni arco $(u, v)$ si ha:
	- $(u, v)$ è un arco dell'albero DFS, oppure 
	- i nodi $u$ e $v$ sono l'uno discendente/antenato dell'altro, oppure
	- $(u, v)$ è un arco trasversale a sinistra, ovvero il vertice $v$ è in un sottoalbero visitato precedentemente ad $u$

