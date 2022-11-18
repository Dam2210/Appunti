## Ordinamento

>Dato un insieme S di n oggetti presi da un dominio totalmente ordinato, ordinare S.

- Esempi: ordinare una lista di nomi alfabeticamente, o un insieme di numeri, o un insieme di compiti d'esame in base al cognome dello studente.
- Subroutine in molti problemi
- E' possibile effettuare ricerche in array ordinati in tempo *O(log n )*

## Il problema dell'ordinamento

- Input: una sequenza di n numeri <$a_{1}, \ a_{2}, \ ..., \ a_{n}$>
- Output: una permutazione (riarrangiamento) <$a_{1}', \ a_{2}', \ ..., \ a_{n}'$> della sequenza di input tale che $a_{1}' \leq a_{2}'\leq ...\leq a_{n}'$ 

## Ordinare in tempo quadratico

>Un algoritmo semplice, intuitivo, facile da programmare. E inefficiente.

### Selection Sort

Approccio incrementale: estende l'ordinamento da k a k+1 elementi, scegliendo il minimo degli n-k elementi non ancora ordinati e mettendolo in posizione k+1.

![[immagine5.png]]

![[immagine6.png]]
- Al generico passo k, A[1], ..., A[k] sono già ordinati 
- linee 2-4: ricerca del minimo fra gli elementi A[k+1], ..., A[n]
- m è l'indice dell'array in cui si trova il minimo 
- Il minimo è messo in posizione k+1

### Corretto?

- E' facile convincersi che l'algoritmo mantiene le seguenti *invarianti*: dopo il generico passo k (k=0, ..., n-2) abbiamo che:
	1) i primi k+1 elementi sono ordinati.
	2) sono i k+1 elementi più piccoli dell'array.

>Suggerimento: ragionare per invarianti è uno strumento utile per dimostrare la correttezza di un algoritmo, perchè permette di isolare proprietà dell'algoritmo, spiegarne il funzionamento, capire a fondo l'idea su cui si basa.

## Complessità temporale (analisi)

T(n) = # operazioni elementari sul modello RAM a costi uniformi eseguite 
dall'algoritmo nel caso peggiore su istanze di dimensione n.

### Complessità: un upper bound

![[immagine7.png]]

$$T(n)\leq 5n^{2} \ O(1) = \Theta(n^{2}) \rightarrow \ T(n) = O(n^2)$$ 
>L'analisi è stretta? Cioè, $T(n)$ è $\Theta(n^{2})$  

### Complessità: un lower bound

![[immagine8.png]]

$$T(n)\geq\sum_{k=0} ^ {n-2}(n-k-1) = \sum_{k=1} ^ {n-1}k=n(n-1)/2 = \Theta(n^{2})$$
$$\rightarrow T(n) = \Omega(n^{2})\rightarrow T(n) = \Theta(n^{2})$$
## Altri algoritmi di ordinamento con tempo $O(n^{2})$

### Insertion Sort

Approccio incrementale: estende l'ordinamento da k a k+1 elementi, posizionando l'elemento (k+1)-esimo nella posizione corretta rispetto ai primi k elementi.

![[immagine9.png]]

### Bubble Sort

Approccio incrementale: esegue n-1 scansioni. Ad ogni scansione guarda coppie di elementi adiacenti e li scambia se non sono nell'ordine corretto.

![[immagine10.png]]

>ESERCIZIO: Scrivere lo pseudocodice dei due algoritmi e fare l'analisi della complessità temporale nel caso peggiore.

## Ordinare in tempo meno che quadratico

>Un algoritmo semplice, un po' meno intuitivo, facile da programmare. E temporalmente efficiente.
>Tecnica: Divide et Impera.

### MergeSort

- Usa la tecnica del Divide et Impera:
	1) Divide: dividi l'array a metà
	2) Risolvi i due sottoproblemi ricorsivamente
	3) Impera: fondi le due sottosequenze ordinate

![[immagine11.png]]

### Esempio di esecuzione:

![[immagine12.png]]

## Procedura Merge

- Due array ordinati A e B possono essere fusi rapidamente:
	- Estrai ripetutamente il minimo di A e B e copialo nell'array di output, finchè A oppure B non diventa vuoto.
	- Copia gli elementi dell'array non vuoto alla fine dell'array di output.

>Nota: dato un array A e due indici $x\leq y$ , denotiamo con A[x ; y] la porzione di A costituita da A[x],  A[x+1], ..., A[y].

![[immagine13.png]]
![[immagine14.png]]
![[immagine15.png]]
![[immagine16.png]]
![[immagine17.png]]
![[immagine18.png]]
![[immagine19.png]]
![[immagine20.png]]
![[immagine21.png]]
![[immagine22.png]]

>Lemma: la procedura Merge fonde due sequenze ordinate di lunghezza $n_{1}$ e $n_{2}$ in tempo $\Theta(n_{1}+n_{2})$ 

Dim:
Ogni confronto "consuma" un elemento di una delle due sequenze. Ogni posizione di X è riempita in tempo costante. Il numero totale di elementi è $n_{1}+n_{2}$. Anche la Linea 12 (copia del vettore ausiliario) costa $\Theta(n_{1}+n_{2})$.

![[immagine23.png]]

Corretto?
Si.
- Chiamate ricorsive ordinano le due metà.
- Il Merge le fonde correttamente.

Complessità?

### Tempo di esecuzione

- La complessità temporale del MergeSort è descritto dalla seguente relazione di ricorrenza:
$$T(n) = 2T(n/2)+O(n)$$
- Usando il Teorema Master si ottiene:
$$T(n)=O(n \ logn)$$
$$a=b=2,\ f(n)=O(n)\rightarrow caso \ 2$$
## Quanta memoria (ausiliaria) usiamo?

- La complessità spaziale del MergeSort è $\Theta(n)$:
	- La procedura Merge usa memoria ausiliaria pari alla dimensione di porzione da fondere;
	- Non sono mai attive due procedure di Merge contemporaneamente;
	- Ogni chiamata di MergeSort usa memoria costante (esclusa quella usata dalla procedura Merge);
	- Numero di chiamate di MergeSort attive contemporaneamente sono $O(n\ logn)$

- Il MergeSort non ordina in loco
	- Occupazione di memoria ausiliaria (oltre input) pari a $\Theta(n)$

## Ancora un algoritmo di ordinamento che usa la tecnica del divide et impera: il QuickSort

>Efficiente?
>Caso peggiore, caso medio e versione randomizzata.

### Quicksort

- Usa la tecnica del divide et impera:
	1) Divide: scegli un elemento x della sequenza (perno) e partiziona la sequenza in elementi $\leq x$ ed elementi $>x$.
	2) Risolvi i due sottoproblemi ricorsivamente.
	3) Impera: restituisci la concatenazione delle due sottosequenze ordinate.

>Rispetto al MergeSort, divide complesso ed impera semplice.

### Partizione (in loco)

- Scegli il perno
- Scorri l'array "in parallelo" da sinistra verso destra e da destra verso sinistra
	- da sinistra verso destra, ci si ferma su un elemento maggiore del perno
	- da destra verso sinistra, ci si ferma su un elemento minore del perno
- Scambia gli elementi e riprendi la scansione

### Partizione in loco: un esempio

![[immagine24.png]]
![[immagine25.png]]

>Proprietà (invariante):
>In ogni istante, gli elementi A[i], ..., A[inf-1] sono $\leq$ del perno, mentre gli elementi A[sup+1], ..., A[f] sono $>$ del perno.

![[immagine26.png]]

## Esempio di esecuzione

>L'albero delle chiamate ricorsive può essere sbilanciato.

![[immagine27.png]]
![[immagine28.png]]

Corretto?
Si.
- Dopo Partition:
	A[i:m-1] contiene elem $\leq$ del perno, A[m] il perno, A[m+1:f] elementi $>$ del perno.
- Le chiamate ricorsive ordinano A[i:f]

Complessità?

### Analisi nel caso peggiore

- Ogni invocazione di Partition posizione almeno un elemento in modo corretto (il perno).
- Quindi dopo $n$ invocazioni di Partition, ogniuna di costo $O(n)$ ho il vettore ordinato. Il costo complessivo è quindi $O(n^{2})$ .

- Il caso peggiore si verifica quando il perno scelto ad ogni passo è il minimo o il massimo degli elementi nell'array.
- La complessità in questo caso è:
$$\begin{align} 
T(n) &=T(n-1)+T(0)+O(n)\\
&=T(n-1)+O(1)+O(n)\\
&=T(n-1)+O(n)\\
\\ 
&\rightarrow T(n)=O(n^{2})
\end{align}
$$

Complessità nel caso migliore?
Caso migliore: $O(n \ logn)$, partizionamento sempre bilanciato.

![[immagine29.png]]

## ...Intuizioni sul caso medio...

- **Problema**: la partizione può essere sbilanciata.
- La probabilità che ad ogni passo si presenti la partizione peggiore è molto bassa.
- Per partizioni che non sono "troppo sbilanciate" l'algoritmo è veloce
- **Domanda**: quale è la complessità dell'algoritmo supponendo che l'algoritmo di partizionamento produca sempre una partizione 9-a-1?
- E se la partizione fosse sempre proporzionale 99-a-1?
- **NOTA**: sembrano partizioni piuttosto sbilanciate...

...La complessità è ancora $O(n \ logn)$:

![[immagine30.png]] 
... e se le istanze non sono equiprobabili?

*Versione randomizzata*: scegli il perno $x$ a caso fra gli elementi da ordinare

>Teorema:
>L'algoritmo QuickSort randomizzato ordina in loco un array di lunghezza $n$ in tempo $O(n^{2})$ nel caso peggiore e $O(n \ logn)$ con alta probabilità, ovvero con probabilità almeno $1-1/n$. 

## QuickSort randomizzato 
## (randomizzazione $\neq$ caso medio)

- Nesuna assunzione sulla distribuzione di probabilità delle istanze.
- Nessun input specifico per il quale si verifica il caso peggiore.
- Il caso peggiore determinato solo dal generatore di numeri casuali.



