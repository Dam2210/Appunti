## Progettare algoritmi veloci usando strutture dati efficienti

### HeapSort: l'idea

- Stesso approccio incrementale del SelectionSort
	- seleziona gli elementi dal più grande al più piccolo
	- usa una struttura dati efficiente: estrazione in tempo $O(log  \ n)$ del massimo.

### HeapSort

- Tipo di dato
	- Specifica una collezione di oggetti e delle operazioni di interesse su tale collezione (es. Dizionario: mantiene un insieme di elementi con chiavi soggetto a operazioni di inserimento, cancellazione, ricerca).
- Struttura dati
	- Organizzazione dei dati che permette di memorizzare la collezione e supportare le operazioni di un tipo di dato usando meno risorse di calcolo possibile.

>Cruciale: progettare una struttura dati H su cui eseguire efficientemente le operazioni:
>- Dato un array A, generare velocemente H 
>- Trovare il più grande oggetto in H
>- Cancellare il più grande oggetto da H

- Tipo di dato associato: coda con priorità.

## Alberi: qualche altra definizione

![[immagine33.png]]

>albero d-ario: albero in cui tutti i nodi interni hanno (al più) d figli
>$d=2 \rightarrow albero \ binario$ 
>un albero d-ario è completo: se tutti i nodi interni hanno esattamente d figli e le foglie sono tutte allo stesso livello.

![[immagine34.png]]

- Struttura dati heap associa ad un insieme S = albero binario radicato con le seguenti proprieta:
	1. Completo fino al penultimo livello (struttura rafforzata: foglie sull'ultimo livello tutte compatte a sinistra).
	2. Gli elementi di S sono memorizzati nei nodi dell'albero (ogni nodo v memorizza uno e un solo elemento, denotato con chiave(v)).
	3. $chiave(padre(v))\geq chiave(v)$ per ogni nodo v diverso dalla radice.

![[immagine35.png]]

## Proprietà salienti degli heap

1. Il massimo è contenuto nella radice.
2. L'albero con n nodi ha altezza $O(log \ n)$.
3. Gli heap con struttura rafforzata possono essere rappresentati in un array di dimensione pari a n.

![[immagine36.png]]
![[immagine37.png]]
![[immagine38.png]]

## La procedura fixHeap

Sia v la radice di H. Assume che i sottoalberi radicati nel figlio sinistro e destro di v sono heap, ma la proprietà di ordinamento delle chiavi non vale per v. Posso ripristinarla così:

$$
\begin{align}
fixHeap &(nodo \ v, \ heap \ H)\\
&if(v \ non \ è \ una \ foglia) \ then\\
&\ \ \ \ \ sia \ u \ il \ figlio \ di \ v \ con \ chiave \ massima\\
&\ \ \ \ \ if(chiave(v) < chiave(u)) \ then\\
&\ \ \ \ \ \ \ \ \ \ \ \ scambia \ chiave(v) \ e \ chiave(u)\\
&\ \ \ \ \ \ \ \ \ \ \ \ fixHeap(u,\ H)
\end{align}
$$
>Tempo di esecuzione: $O(log \ n)$

## fixHeap esempio:

 ![[immagine39.png]]
![[immagine40.png]]
![[immagine41.png]]
![[immagine42.png]]
![[immagine43.png]]

Uno pseudocodice di fixHeap più dettagliato (l'heap è mantenuto attraverso un vettore posizionale):

![[immagine44.png]]

## Estrazione del massimo

- Copia nella radice la chiave contenuta nella foglia più a destra dell'ultimo livello
>nota: è l'elemento in posizione heap-size

- Rimuove la foglia
>nota: nella rappresentazione con vettore posizionale vuol dire decrementare heap-size.

- Ripristina la proprietà di ordinamento a heap richiamando fixHeap sulla radice

Tempo di esecuzione $O(log \ n)$

![[immagine45.png]]
![[immagine46.png]]
![[immagine47.png]]

## Costruzione dell'heap

Algoritmo ricorsivo basato dulla tecnica del divide et impara:

$$
\begin{align}
heapify&(heap \ H)\\
&if(H \ non \ è \ vuoto) \ then\\
&\ \ \ \ heapify(sottoalbero \ sinistro \ di \ H)\\
&\ \ \ \ heapify(sottoalbero \ destro \ di \ H)\\
&\ \ \ \ fixHeap(radice \ di \ H, \ H)
\end{align}
$$

## Heapify - Un esempio

![[immagine48.png]]
![[immagine49.png]]
![[immagine50.png]]
![[immagine51.png]]

## Complessità heapify

Sia h l'altezza di un heap con $n$ elementi.
Sia $n' \geq n$ l'intero tale che un heap con $n'$ elementi ha:
1. altezza h
2. è completo fino all'ultimo livello

Vale: $T(n) \leq T(n')$ e $n' \leq 2n$ 


Tempo di esecuzione:
$$
\begin{align}
T(n')&=2T((n'-1)/2)+O(log \ n')\\
&\leq 2T(n'/2)+O(log \ n')\\
\\
&\rightarrow T(n')=O(n') \ dal \ teorema \ Master\\
&Quindi: T(n)\leq T(n')=O(n')=O(2n)=O(n)
\end{align}
$$

## Max-Heap e Min-Heap

E se volessi una struttura dati che mi permette di estrarre il minimo velocemente invece del massimo?

Semplice: costruisco un min-heap invertendo la proprietà di ordinamento delle chiavi. Cioè richiedo che $chiave(padre(v)) \leq chiave(v)$ per ogni $v$ (diverso dalla radice).

## L'algloritmo HeapSort

- Costruisce un heap tramite heapify
- Estrae ripetutamente il massimo per $n-1$ volte
	- ad ogni estrazione memorizza il massimo nella posizione dell'array che si è appena liberata.

![[immagine52.png]]

### Esempio:
![[immagine53.png]]
![[immagine54.png]]
![[Immagine55.png]]
![[immagine56.png]]
![[immagine57.png]]
![[immagine58.png]]
![[immagine59.png]]
![[immagine60.png]]![[immagine61.png]]
![[immagine62.png]]
![[immagine63.png]]
![[immagine64.png]]

## Max-Heap e Min-Heap

Quindi: come mai abbiamo usato un max-heap e non un min-heap? Potevamo usare anche un min-heap?

L'uso del max-heap (implementato con un vettore posizionale) ci permette di usare solo memoria ausiliare costante.

>Teorema:
>L'algoritmo HeapSort ordina in loco un array di lunghezza $n$ in tempo $O(n \ logn)$ nel caso peggiore.

