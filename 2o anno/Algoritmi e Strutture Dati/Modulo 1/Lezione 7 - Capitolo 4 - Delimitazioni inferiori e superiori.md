
## Delimitazioni superiori (upper bound)

>Definizione:
>Un algoritmo A ha complessità (costo di esecuzione) $O(f(n))$ rispetto ad una certa risorsa di calcolo, se la quantità $r(n)$ di risiorsa usata da A nel caso peggiore su istanze di dimensione $n$ verifica la relazione $r(n) = O(f(n))$.

>Definizione:
>Un problema P ha complessità $O(f(n))$ rispetto ad una risorsa di calcolo se esiste un algoritmo che risolve P il cui costo di esecuzione rispetto quella risorsa è $O(f(n))$.

## Delimitazioni inferiori (lower bound)

>Definizione: 
>Un algoritmo A ha complessità (costo di esecuzione) $\Omega(f(n))$ rispetto ad una certa risorsa di calcolo, se la quantità $r(n)$ di risorsa usata da A nel caso peggiore su istanze di dimensione $n$ verifica la relazione $r(n)=\Omega(f(n))$.

>Definizione:
>Un problema P ha una complessità $\Omega(f(n))$ rispetto ad una risorsa di calcolo se ogni algoritmo che risolve P ha costo di esecuzione nel caso peggiore $\Omega(f(n))$ rispetto quella risorsa

## Ottimalità di un algoritmo

>Definizione:
>Dato un problema P con complessità $\Omega(f(n))$ rispetto ad una risorsa di calcolo, un algoritmo che risolve P è (asintoticamente) ottimo se ha costo di esecuzione $O(f(n))$ rispetto a quella risorsa.

## Complessità temporale del problema dell'ordinamento

- Upper bound: $O(n^2)$
	- Insertion Sort, Selection Sort, Quick Sort, Bubble Sort
- Un upper bound migliore: $O(n \ log \ n)$ 
	- Merge Sort, Heap Sort
- Lower bound: $\Omega(n)$ 
	- banale: ogni algoritmo che ordina n elementi li deve almeno leggere tutti.

Possiamo fare di meglio?

Sui limiti della velocità: una delimitazione inferiore (lower bound) alla complessità del problema

>Ordinamento per confronti:
>Dati due elementi $a_i$ ed $a_j$, per determinare l'ordinamento relativo effettuiamo una delle seguenti operazioni di confronto:
>$$a_i < a_j \ ; \ a_i\leq a_j \ ; \ a_i = a_j \ ; \ a_i\geq a_j \ ; \ a_i>a_j$$
>Non si possono esaminare i valori degli elementi o ottenere informazioni sul loro ordine in altro modo.

Notare: Tutti gli algoritmi citati prima sono algoritmi di ordinamento per confronto.

>Teorema:
>Ogni algoritmo basato su confronti che ordina $n$ elementi deve fare nel caso peggiore $\Omega(n \ log \ n)$ confronti.

NOTA: il # di confronti che un algoritmo esegue è un lower bound al # di passi elementari che esegue.

Corollario:
Il Merge Sort e l'Heap Sort sono algoritmi ottimi (almeno dentro la classe di algoritmi basati su confronti).

## Uno strumento utile: albero di decisione

Gli algoritmi di ordinamento per confronto possono essere descritti in modo astratto in termini di alberi di decisione.

Un generico algoritmo di ordinamento per confronto lavora nel modo seguente:
- Confronta due elementi $a_i$ ed $a_j$ (ad esempio effettua il test $a_i \leq a_j$);
- A seconda del risultato - riordina e/o decide il confronto successivo da eseguire.

>Albero di decisione:
>Descrive i confronti che l'algoritmo esegue quando opera su un input di una determinata dimensione. I movimenti dei dati e tutti gli altri aspetti dell'algoritmo vengono ignorati.

## Alberi di decisione

- Descrive le diverse sequenze di confronti che A  potrebbe fare su istanze di dimensione $n$.
- Nodo interno (non foglia): {$i:j$}
	- modella il confronto tra $a_i$ e $a_j$
- Nodo foglia: 
	- modella una risposta (output) dell'algoritmo: permutazione degli elementi.

![[immagine95.png]]

Osservazioni:
- L'albero di decisione non è associato ad un problema.
- L'albero di decisione non è associato solo ad un algoritmo.
- L'albero di decisione è associato ad un algoritmo e a una dimensione dell'istanza.
- L'albero di decisione descrive le diverse sequenze di confronti che un certo algoritmo può eseguire su istanze di una data dimensione.
- L'albero di decisione è una descrizione alternativa dell'algoritmo (customizzato per istanze di una certa dimensione).

Esempio:
Fornire l'albero di decisione del seguente algoritmo per istanze di dimensione 3.

![[immagine96.png]]

Soluzione:

![[immagine97.png]]

Proprietà:

- Per una particolare istanza, i confronti eseguiti dall'algoritmo su quella istanza rappresentano un cammiano radice - foglia
- L'algoritmo segue un cammino diverso a seconda delle caratteristiche dell'istanza 
	- Caso peggiore: cammino più lungo.
- Il numero di confronti nel caso peggiore è pari all'altezza dell'albero di decisione
- Un albero di decisione di un algoritmo (corretto) che risolve il problema nell'ordinamento di $n$ elementi deve avere necessariamente almeno $n!$ foglie

>Lemma:
>Un albero binario T con k foglie, ha altezza almeno $log_2 \ k$ 

dim (per induzione sul k):
caso base: $k = 1$, altezza almeno $log_2 \ 1 = 0$ 
caso induttivo: $k>1$ 
considera il nodo interno v più vicino alla radice che ha due figli (v potrebbe essere la radice). Nota che v deve esistere perchè $k>1$.

v ha almeno un figlio u che è radice di un (sotto) albero che ha almeno $k/2$ foglie e $<k$ foglie.

T ha altezza almeno:
$1+log_2 \ k/2=1+log_2 \ k - log_2 \ 2=log_2 \ k$ 

## Il lower bound $\Omega(n \ logn)$ 

- Consideriamo l'albero di decisione di un qualsiasi algoritmo che risolve il problema dell'ordinamento di n elementi
- L'altezza h dell'albero di decisione è almeno $log_2 (n!)$ 
- Formula di Stirling: $n! \approx (2 \pi n)^{1/2}(n/e)^n$ 

$$
\begin{align}
h \geq log_2(n!)&>log_2(n/e)^n=\\
&=n \ log_2(n/e)= \\
n!>(n/e)^n &= n \ log_2n-n \ log_2 e= \\
& = \Omega(n \ logn) 
\end{align}
$$

Può un algoritmo basato su confronti ordinare n interi piccoli, diciamo compresi fra 1 e $k = O(n)$, in (asintoticamente) meno di $n \ logn$?

no, la dimostrazione funziona anche sotto questa ipotesi!

## IntegerSort: fase 1

Per ordinare $n$ interi con valori in $[1,k]$ 
Mantiene un array $Y$ di $k$ contatori tale che $Y[x]$ = numero di volte che il valore $x$ compare nell'array di input $X$.

![[immagine98.png]]

## IntegerSort: fase 2

Scorre $Y$ da sinistra verso destra e, se $Y[x]=k$, scrive in $X$ il valore $x$ per $k$ volte.

![[immagine99.png]]
![[immagine100.png]]

## IntegerSort: analisi

- Tempo $O(1)+O(k)=O(k)$ per inizializzare $Y$ a 0.
- Tempo $O(1)+O(n)=O(n)$ per calcolare i valori dei contatori.
- Tempo $O(n+k)$ per costruire X.
	- $\rightarrow O(n+k)$ 
	- tempo lineare se $k = O(n)$ 
Contraddice il lower bound di $\Omega(n \ logn)$?
No, perchè l'IntegerSort non è un algoritmo basato sui confronti!
