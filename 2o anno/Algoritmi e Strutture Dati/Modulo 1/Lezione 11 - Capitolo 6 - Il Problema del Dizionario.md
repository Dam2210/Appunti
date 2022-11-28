
## Il problema del dizionario

![[immagine170.png]]

### Come implementare efficientemente un dizionario?

è possibile granatire che tutte le operazioni su un dizionario di $n$ elementi abbiano tempo $O(log \ n)$ 

Due idee:
- Alberi binari di ricerca:
	- Definire un albero (binario) tale che ogni operazione richiede tempo $O(altezza \ albero)$ 
- Alberi AVL:
	- Fare in modo che l'altezza dell'albero sia sempre $O(log \ n)$ 

## Alberi binari di ricerca (BST = binary search tree)

> Definizione:
> Albero binario che soddisfa le seguenti proprietà:
> - Ogni nodo $v$ contiene un elemento $elem(v)$ cui è associata una chiave $chiave(v)$ presa da un dominio totalmente ordinato.
> Per ogni nodo $v$ vale che:
> - Le chiavi nel sottoalbero sinistro di $v$ sono $\leq chiave(v)$ 
> - Le chiavi nel sottoalbero destro di $v$ sono $> chiave(v)$ 

Esempi:

![[immagine171.png]]

ancora un esempio...

![[immagine172.png]]

... Che succede se visitiamo un BST in ordine simmetrico?

![[immagine173.png]]

Verifica di correttezza:
Indichiamo con $h$ l'altezza dell'albero.
Vogliamo mostrare che la vista in ordine simmetrico restituisce la sequenza ordinata.

Per induzione sull'altezza dell'ABR: $h = 1$ 
(mostriamolo senza perdita di generalità quando l'albero è completo.)

![[immagine174.png]]

Verifica correttezza (continua...)
$h =$ generico (ipotizzo che la procedura sia corretta per altezza $<h$)

![[immagine175.png]]

## ... Implementare le operazioni del dizionario (search, insert e delate) su un BST

### $search(chiave \ k) \rightarrow elem$:

Traccia un cammino nell'albero partendo dalla radice: su ogni nodo, usa la proprietà di ricerca per decidere se proseguire nel sottoalbero sinistro o destro.

![[immagine176.png]]
![[immagine177.png]]

### $insert(elem \ e, \ chiave \ k)$:

Idea: aggiunge la nuova chiave come nodo foglia;
per capire dove mettere la foglia simula una ricerca con la chiave da inserire

1. Crea un nuovo nodo $u$ con $elem = e$ e $chiave=k$.
2. Cerca la chiave $k$ nell'albero, identificando così il nodo $v$ che diventerà padre di $u$.
3. Appendi $u$ come figlio sinistro/destro  di $v$ in modo che sia mantenuta la proprietà di ricerca.

![[immagine178.png]]

Correttezza:
Se seguo questo schema l'elemento $e$ viene posizionato nella posizione giusta. Infatti, per costruzione, ogni antenato di $e$ si ritrova $e$ nel giusto sottoalbero.

## ... Qualche operazione ausiliaria prima di implementare l'operazione di delete: massimo, minimo, predecessore e successore

### Ricerca del massimo:

![[immagine179.png]]

>Nota: è possibile definire una procedura $main(nodo \ u)$ in maniera del tutto analoga

![[immagine180.png]]

### Predecessore e successore:

- Il predecessore di un nodo $u$ in un BST è il nodo $v$ nell'albero avente massima chiave $\leq chiave(v)$ 
- Il successore di un nodo $u$ in un BST è il nodo $v$ nell'albero avente minima chiave $\geq chiave(v)$ 
- Come trovo il predecessore/successore di un nodo in un BST?

![[immagine181.png]]

>Nota: la ricerca del successore di un nodo è simmetrica:

![[immagine182.png]]

### delete(elem \ e):

Sia $u$ il nodo contenete l'elemento $e$ da cancellare:
1) $u$ è una foglia: rimuovila
2) $u$ ha un solo figlio:

![[immagine183.png]]

3) $u$ ha due figli: sostituiscilo con il predecessore (o successore) ($v$) e rimuovi fisicamente il predecessore (o successore) (che ha al più un figlio):

![[immagine184.png]]
![[immagine185.png]]

## Costo delle operazioni:

- Tutte le operazioni hanno costo $O(h)$ dove $h$ è l'altezza dell'albero.
- $O(n)$ nel caso peggiore (alberi molto sbilanciati e profondi)

... Un albero binario di ricerca bilanciato ...
$h = O(log \ n)$ 

![[immagine186.png]]
![[immagine187.png]]

## Il problema del dizionario

![[immagine188.png]]

### Come implementare efficientemente un dizionario?

è possibile garantire che tutte le operazioni du un dizionario di $n$ elementi abbiano tempo $O(log \ n)$.

Due idee:
- Alberi binari di ricerca:
	- Definire un albero (binario) tale che ogni operazione richiede tempo $O(altezza \ albero)$ 
- Alberi AVL:
	- Fare in modo che l'altezza dell'albero sia sempre $O(log \ n)$

## Alberi AVL (Adel'son-Vel'skii e Landis, 1962)

>Definizioni:
>
>Fattore di bilanciamento $\beta (v)$ di un nodo $v$ = altezza del sottoalbero sinistro di $v$ - altezza del sottoalbero destro di $v$. 
>
>Un albero si dice ==bilanciato in altezza== se ogni nodo $v$ ha fattore di bilanciamento in valore assoluto $\leq 1$.
>
>Alberi AVL = alberi binari di ricerca bilanciati in altezza.
>
>Generalmente $\beta (v)$ mantenuto come informazione addizionale nel record relativo a $v$

... Qualche esempio ...

![[immagine189.png]]
![[immagine190.png]]
![[immagine191.png]]

## Altezza di alberi AVL

Si può dimostrare che un albero AVL con $n$ nodi ha altezza $O(log \ n)$.

Idea della dimostrazione: considerare, tra tutti gli AVL, i più sbilanciati.

Albero di Fibonacci di altezza $h$:
albero AVL di altezza $h$ con il minimo numero di nodi $n_h$.

minimizzare il numero di nodi fissata l'altezza è uguale a massimizzare l'altezza fissato il numero di nodi.

Intuizione: Se gli alberi di Fibonacci hanno altezza $O(log \ n)$ allora tutti gli alberi AVL hanno altezza $O(log \ n)$.

Un esempio:
Come è fatto un albero di Fibonacci di altezza 2?

![[immagine192.png]]

... Alberi di Fibonacci per valori piccoli di altezza ...

![[immagine193.png]]
![[immagine194.png]]
![[immagine195.png]]

Posso usare un albero AVL per implementare un dizionario?

![[immagine196.png]]

Domanda:
di quanto e quali fattori di bilanciamento cambiano a fronte di un inserimento/cancellazione?

Se parto da un albero AVL e inserisco/cancello un nodo:
- (quali) cambiano solo i fattori di bialnciamnto dei nodi lungo il cammino radice-nodo inserito/cancellato
- (quanto) i fattori di bilanciamento cambiano di +/- 1

## Implementazione delle operazioni

- L'operazione search procede come in un BST
- Ma inserimenti e cancellazioni potrebbero sbilanciare l'albero
- $\rightarrow$ Manteniamo il bilanciamento tramite opportune rotazioni

## Rotazione di base verso destra/sinistra sul nodo v/u

![[immagine197.png]]

## Ribilanciamnto tramite rotazioni

- Le rotazioni sono effettuate su nodi sbilanciati
- Sia v un nodo di profondità massima (nodo critico) con fattore di bilanciamento $\beta (v) \pm 2$ 
- Esiste un sottoalbero T di v che lo sbilancia
- A seconda della posizione di T si hanno 4 casi:
![[immagine198.png]]
- I quattro casi sono simmetrici a coppie 
$[\beta (v) = \pm 2, \ altezza \ T_1 = h+1]$

## Caso SS

- L'altezza di T(v) è $h+3$, l'altezza di T(u) è $h+2$, l'altezza di $T_3$ è $h$, e l'altezza di $T_1$ è $h+1\rightarrow \beta(v)= +2$ e lo sbilanciamento è provocato da $T_1$ 
![[immagine199.png]]
- Si applica una rotazione semplice verso destra su v; 2 sottocasi possibili:
	1) l'altezza di $T_2$ è $h \rightarrow$ l'altezza dell'albero coinvolto nella rotazione passa da $h+3$ a $h+2$
	2) l'altezza di $T_2$ è $h+1 \rightarrow$ l'altezza dell'albero coinvolto nella rotazione rimane pari a $h+3$
![[immagine200.png]]

## Osservazioni sul caso SS

- Dopo la rotazione l'albero è bilanciato (tutti i fattori di bilanciamento sono in modulo $\leq 1$)
- L'inserimento di un elemento nell'AVL (ovvero, l'aggiunta di una foglia a un albero bilanciato) può provocare solo il sottocaso 1) (perchè altrimenti l'AVL era già sbilanciato!)
- Invece, la cancellazione di un elemento dall'AVL (che necessariemente fa diminuire l'altezza di qualche sottoalbero) può provocare entrambi i casi (ad esempio, se cancello un elemento ho abbassato l'altezza di $T_3$)
- Nel caso 1), dopo la rotazione, l'albero diminuisce la sua altezza di uno
$[\beta(v)=+2, \ altezza \ T_1 = h]$ (che implica altezza T(w) = $h+1$)

## Caso SD

- l'altezza di T(v) è $h+3$, laltezza di $T(z)$è $h+2$, l'altezza di $T_1$ è $h$, l'altezza di $T_4$ è $h$, e l'altezza di $T(w)$ è $h+1 \rightarrow$ $\beta(v)=+2$ e $\beta(z)=-1$ cioè lo sbilanciamento è provocato dal sottoalbero destro di $z$.
![[immagine201.png]]
- Applicare due rotazioni semplici: una verso sinistra sul figlio sinistro del nodo critico (nodo z), l'altra verso destra sul nodo critico (nodo v).

## Caso SD

