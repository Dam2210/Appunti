
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