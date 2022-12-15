
## Tipo di dato CodaPriorità (1/2

![[immagine212.png]]

## Tipo di dato CodaPriorità (2/2)

![[immagine213.png]]

Applicazioni: gestione code in risorse condivise, gestione priorità in processi concorrenti, progettazione di algoritmi efficienti per diversi problemi fondamentali (es: calcolo cammini minimi in un grafo, minimo albero ricoprente, ordinamento, ecc.)

## Quattro implementazioni elementari

1. Array non ordinato
2. Array ordinato
3. Lista non ordinata
4. Lista ordinata

Ci focalizzeremo soltanto sulle operazioni di base.

## Array non ordinato

Lo dimensiono sufficientemente grande e tengo traccia del numero $n$ di elementi nella coda in una variabile di appoggio.

- $FindMin: \Theta(n)$ (devo guardare tutti glielementi)
- $Insert: O(1)$ (inserisco in coda)
- $Delete: O(1)$ (poichè mi viene fornito il riferimento diretto all'elemento da cancellare, lo posso cancellare in $O(1)$ sovracopiando l'ultimo elemento)
- $DeleteMin: \Theta(n)$ (devo prima cercare il minimo in $\Theta(n)$, poi lo posso cancellare in $O(1)$)

## Array ordinato

Lo dimensiono sufficientemente grande, lo tengo ordinato in ordine decrescente e tengo traccia del numero $n$ di elmenti nella coda in una variabile di appoggio.

- $FindMin: O(1)$ 
- $Insert: O(n)$ (trovo il minimo in $\Theta(log \ n)$ la giusta posizione, ma poi devo fare $O(n)$ spostamenti)
- $Delete: O(n)$ (devo fare $O(n)$ spostamenti)
- $DelateMin: O(1)$ (l'elemento minimo è in fondo all'array, non devo fare spostamenti)

## Lista non ordinata

![[immagine214.png]]

- $FindMin: \Theta(n)$ (devo guardare tutti gli elementi)
- $Insert: O(1)$ (inserisco in coda o in testa)
- $Delete: O(1)$ (poichè mi viene fornito il riferimento diretto all'elemento da cancellare, lo posso cancellare in $O(1)$ agendo sui puntatori)
- $DeleteMin: \Theta(n)$ (devo prima cercare il minimo in $\Theta(n)$, poi lo posso cancellare in $O(1)$)

## Array ordinato

Lo dimensiono sufficientemente grande, lo tengo ordinato in ordine decrescente e tengo traccia del numero $n$ di elementi nella coda in una variabile di appoggio.

- $FindMin: O(1)$
- $Insert: O(n)$ (trovo in $\Theta(log \ n)$ la giusta posizione, ma poi devo fare $O(n)$ spostamenti)
- $Delete: O(n)$ (devo fare $O(n)$ spostamenti)
- $DeleteMin: O(1)$ (l'elemento minimo è in fondo all'array, non devo fare spostamenti)

## Lista non ordinata

![[immagine215.png]]

- $FindMin: \Theta(n)$
- $Insert: O(1)$ (inserisco in coda o in testa)
- $Delete: O(n)$ (poichè mi viene fornito il riferiemento diretto all'elemento da cancellare, lo posso cancellare in $O(1)$ agendo sui puntatori)
- $DeleteMin: \Theta(n)$ (devo prima cercare il minimo in $\Theta(n)$, poi lo posso cancellare in $O(1)$)

## Lista ordinata

Tengo la lista bidirezionale ordinata in ordine crescente

- $FindMin: O(1)$ (il minimo è in testa alla lista)
- $Insert: O(n)$ (trovo in $O(n)$ la giusta posizione, e poi faccio in $O(1)$ l'inserimento)
- $Delete: O(1)$ (agisco sui puntatori)
- $DeleteMin: O(1)$ (basta far puntare la testa dalla lista al secondo elemento della lista stessa)

![[immagine216.png]]

## Tre implementazioni evolute

$\rightarrow$ d-heap: generalizzazione degli heap binari visti per l'ordinamento
$\rightarrow$ Heap binomiali
$\rightarrow$ Heap di Fibonacci (cenni)

## d-heap

>Definizione:
>Un d-heap è un albero radicato d-ario con le seguenti proprietà:
>1. Struttura: è completo almeno fino al penultimo livello, e tutte le foglie sull'ultimo livello sono compattate verso sinistra.
>2. Contenuto informativo: ogni nodo $v$ contiene un elemento $elem(v)$ ed una chiave $chiave(v)$ presa da un dominio totalmente ordinato
>3. Ordinamento parziale (inverso) dell'heap (min-heap): $chiave(v)\geq chiave(parent(v))$ per ogni nodo $v$ diverso dalla radice.

Esempio:

![[immagine217.png]]

## Proprietà

1. Un d-heap con $n$ nodi ha altezza $\Theta(log_d \ n)$ 
2. La radice contiene l'elemento con chiave minima (per via della priorità di ordinamento a heap)
3. Può essere rappresentato implicitamente tramite vettore posizionale grazie alla proprietà di struttura.

## Procedure ausiliarie

Utili per ripristinare la proprietà di ordinamento a heap su un nodo $v$ che non la soddisfi

![[immagine218.png]]

## findMin

![[immagine219.png]]
![[immagine220.png]]
![[immagine221.png]]
![[immagine222.png]]
![[immagine223.png]]
![[immagine224.png]]

## insert(elem e, chiave k)

Crea un nuovo nodo $v$ con elemento $e$ e chiave $k$, in modo che diventi una foglia sull'ultimo livello di $T$. La proprietà dell'ordinamento a heap viene poi ripristinata spingendo il nodo $v$ verso l'alto tramite ripetuti scambi di nodi.
$$T(n) = O(log_d \ n)$$
per l'esecuzione di muoviAlto

![[immagine225.png]]
![[immagine226.png]]
![[immagine227.png]]
![[immagine228.png]]
![[immagine229.png]]
![[immagine230.png]]
![[immagine231.png]]
![[immagine232.png]]

## delete(elem e) e deleteMin

Scambia il nodo $v$ contente l'elemento $e$ con una qualunque foglia $u$ sull'ultimo livello di $T$, e poi elimina $v$. Ripristina infine la proprietà dell'ordinamento a heap spingendo il nodo $u$ verso la sua posizione corretta scambiandolo riprtutamente con il proprio padre o con il proprio figlio contente la chiave più piccola
$$T(n)=O(log_d \ n) \ oppure \ O(d \ log_d \ n)$$
per l'esecuzione di muoviAlto o muoviBasso

Può essere usata anche per implementare la cancellazione del minimo, con costo $O(d \ log_d \ n)$ 

![[immagine233.png]]
![[immagine234.png]]
![[immagine235.png]]
![[immagine236.png]]
![[immagine237.png]]

## decreaseKey(elem e, chiave d)

Decrementa il valore della chiave nel nodo $v$ contenente l'elemento $e$ della quantità richiesta $d$. Ripristina poi la proprietà dell'ordinamento a heap spingendo il nodo $v$ verso l'alto tramite ripetuti scambi di nodi.
$$T(n)=O(log_d \ n)$$
Per l'esecuzione di muoviAlto

![[immagine238.png]]
![[immagine239.png]]
![[immagine240.png]]
![[immagine241.png]]
![[immagine242.png]]

## increaseKey(elem e, chiave d)

Aumenta il valore della chiave nel nodo contenente l'elemento $e$ della quantità richiesta $d$. Ripristina poi la proprietà dell'ordinamento a heap spingendo il nodo $v$ verso il basso tramite ripetuti scambi di nodi.
$$T(n)=O(d \ log_d \ n)$$
per l'esecuzione di muoviBasso

## merge(CodaPriorità $c_1$, CodaPriorità $c_2$)

Due modi:
1. Costruire da zero: si distruggono le due code e se ne crea una nuova contenente l'unione degli elementi.
2. Inserimenti ripetuti: si inseriscono ripetutamente gli elementi della coda più piccola in quella più grande.

>Oss: nel caso peggiore entrambe le operazioni hanno un costo di $\Omega(n)$

## Costruire da zero 

Idea: 
Genero un nuovo heap d-ario contenente tutti gli elementi in $c_1$ e $c_2$. 

Come:
- Generalizzazione della procedura heapify.
- Rendo i $d$ dottoalberi della radice heap ricorsivamente e chiamo muoviBasso sulla radice.

![[immagine243.png]]

## Inserimenti ripetuti 

Inseriamo ad uno ad uno tutti gli elementi della coda più piccola nella coda più grande.

Sia $k = min\{|c_1|, |c_2|\}$ e $n=|c_1|+|c_2|$.
Eseguiamo quindi $k$ inserimenti nella coda più grande.
Costo: $O(k \ log \ n)$, dove $n=|c_1|+|c_2|$ 
L'approccio conviene quindi per $k \ log \ n = o(n)$, cioè per $k = o(n/log \ n)$.

![[immagine244.png]]

## Alberi Binomiali

Un albero binomiale $B_i$ è definito ricorsivamente come segue:
1. $B_0$ consiste di un unico nodo
2. Per $i>0$, $B_{i+1}$ è ottenuto fondendo due alberi binomiali $B_i$, ponendo la radice dell'uno come figlia della radice dell'altro

![[immagine245.png]]

## Proprietà strutturali

![[immagine246.png]]

## Definizione di heap binomiale

Un heap binomiale è una foresta di alberi binomiali che gode delle seguenti proprietà:
1. Unicità: per ogni intero $i\geq 0$, esiste al più un $B_i$ nella foresta.
2. Contenuto informativo: ogni nodo $v$ contiene un elemento $elem(v)$ ed una chiave $chiave(v)$ presa da un dominio totalmente ordinato
3. Ordinamento a heap: $chiave(v)\geq chiave(parent(v))$ per ogni nodo $v$ diverso da una delle radici.

![[immagine247.png]]
![[immagine248.png]]

## Proprietà topologiche

- Dalla proprietà di unicità degli alberi binomiali che lo costituiscono, ne deriva che un heap binomiale di $n$ elementi è formato dagli alberi binomiali $B_{i_0}$, $B_{i_1}$, ..., $B_{i_h}$, dove $i_0, i_1, ..., i_h$ corrispondonoalle posizioni degli 1 nella rappresentazione in base 2 di $n$.

$\rightarrow$ Ne consegue che in un heap binomiale con $n$ nodi, vi sono al più $\lceil log \ n\rceil$ alberi binomiali, ciascuno con grado ed altezza $O(log \ n)$ 

![[immagine249.png]]

## Procedura ausiliaria

Utile per ripristinare la proprietà di unicità in un heap binomiale (ipotizziamo di scorrere la lista delle radici da sinistra verso destra, in ordine crescente rispetto all'indice degli alberi binomiali)

![[immagine250.png]]
![[immagine251.png]]
![[immagine252.png]]
![[immagine253.png]]
![[immagine254.png]]
![[immagine255.png]]
![[immagine256.png]]
![[immagine257.png]]
![[immagine258.png]]
![[immagine259.png]]

## Heap di Fibonacci

Heap binomiale rilassato: si ottiene da un heap binomiale rilassando la proprietà di unicità dei $B_i$ ed utilizzando un atteggiamento più "pigro" durante l'operazione insert (perchè ristrutturare subito la foresta quando potremmo farlo dopo?)

Heap di Fibonacci: si ottiene da un heap binomiale rilassato indebolendo la proprietà di struttura dei $B_i$ che non sono più necessariamente alberi binomiali

Analisi sofisticata: i tempi di esecuzione sono ammortizzati su sequenze di operazioni, cioè dividendo il costo complessivo della sequenza di operazioni per il numero di operazioni della sequenza 

## Conclusioni: tabella riassuntiva

![[immagine260.png]]

>L'analisi per d-Heap e Heap Binomiali è nel caso peggiore, mentre quella per gli Heap di Fibonacci è ammortizzata (per le operazioni asteriscate)

## Analisi ammortizzata

- Il costo ammortizzato di un'operazione è il costo "medio" rispetto a una sequenza qualsiasi di operazioni.
- Esempio: se un'operazione ha costo ammortizzato costante e eseguo una sequenza (qualsiasi) di $k$ operazioni è possibile che il costo di una singola operazione può essere costante, ma l'intera sequenza costerà $O(k)$. 
- Diverso dal costo medio: non c'è nessuna distribuzione di probabilità (sulla sequenza da eseguire) e l'algoritmo è un algoritmo deterministico.
- Molto utile quando si vogliono buone prestazioni sull'intera sequenza e non garanzie sulla singola operazione 
	- Esempio: progettare algoritmi veloci attraverso strutture dati efficienti

per esempio nel nostro caso...

![[immagine261.png]]

