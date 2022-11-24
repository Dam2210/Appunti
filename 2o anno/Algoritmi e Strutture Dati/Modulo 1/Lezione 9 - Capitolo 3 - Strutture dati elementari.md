## Gestione di collezione di oggetti


Tipo di dato:
- Specifica una collezione di oggetti e delle operazioni di interesse su tale collezione (es. inserisci, cancella, cerca)

Struttura dati:
- Organizzazione dei dati che permette di memorizzare la collezione e supportare le operazioni di un tipo di dato usando meno risorse di calcolo possibile

## Il tipo di dato Dizionario
![[immagine115.png]]

## Il tipo di dato Pila
![[immagine116.png]]

## Il tipo di dato Coda
![[immagine117.png]]

## Tecniche di rappresentazione dei dati

Rappresentazioni indicizzate:
- I dati sono contenuti (principalmente) in array

Rappresentazioni collegate:
- I dati sono contenuti in record collegati fra loro mediante puntatori

## Proprietà

Rappresentazioni indicizzate:
- Array: collezione di celle numerate che contengono elementi di un tipo prestabilito

>Proprietà (forte): gli indici delle celle di un array sono numeri consecutivi.
>Proprietà (debole): non è possibile aggiungere nuove celle ad un array.

Rappresentazioni collegate:
- I costituenti di base sono i record 
- I record dono numerati tipicamente con il loro indirizzo di memoria
- record creati e distrutti individualmente e dinamicamente
- Il collegamento tra un record A e un record B è realizzato tramite un puntatore

>Proprietà (forte): è possibile aggiungere o togliere record a una struttura collegata.
>Proprietà (debole): gli indirizzi dei record di una struttura collegata non sono necessariamente consecutivi.

## Esempi di strutture collegate

![[immagine118.png]]

## Pro e contro

Rappresentazioni indicizzate:
- Pro: accesso diretto ai dati mediante indici
- Contro: dimensione fissa (riallocazione array richiede tempo lineare)

Rappresentazioni collegate:
- Pro: dimensione variabile (aggiunta e rimozione record in tempo costante)
- Contro: accesso sequenziale ai dati

## Realizzazione di un dizionario

Metodo più semplice: array non ordinato (sovradimensionato)
$Insert \rightarrow costa: O(1)$ - inserisco dopo l'ultimo elemento
$Search \rightarrow costa:O(n)$ - devo scorrere l'array
$Delate \rightarrow costa:O(n)$ - delate = search + cancellazione

Array ordinato:
$Search \rightarrow O(log(n))$ - ricerca binaria
$Insert \rightarrow O(n)$ 
				Ho bisogno di:
				$O(log(n))$ confronti $\rightarrow$ per trovare la giusta posizione in cui inserire l'elemento
				$O(n)$ trasferimenti $\rightarrow$ per mantenere l'array ordinato
				(Ricorda che $O(n)+O(log(n))=O(n)$)
$Delate \rightarrow O(n)$ (come per Insert)

...e con le liste?

Lista non Ordinata:
$Search - O(n) \rightarrow$ non posso usare la ricerca binaria
$Insert-O(n)$
$Delate-O(n)$ 

Lista Ordinata
$Search-O(n) \rightarrow$ non posso usare la ricerca binaria
$Insert-O(n) \rightarrow$ devo mantenere ordinata la lista
$Delate-O(n)$ 

------ 

![[immagine119.png]]

-----

## Alberi

### Organizzazione gerarchia dati

![[immagine120.png]]

Dati contenuti nei nodi, relazioni gerarchiche definite dagli archi che li collegano

## Alberi: altre definizioni

![[immagine121.png]]

grado di un nodo: numero dei suoi figli
albero d-ario, albero d-ario completo

u antenato di v se u è raggiungibile da v risalendo di padre in padre 
v discendente di u se u è antenato di v

## Rappresentazioni indicizzate di alberi

Idea: ogni cella dell'array contiene
- Le informazioni di un nodo
- Eventualmente altri indici per raggiungere altri nodi

Vettore dei padri:
Per un albero con $n$ nodi uso un array P di dimensione (almeno) $n$.
Una generica cella $i$ contiene una coppia (info, parent), dove:
- Info: contenuto informativo del nodo $i$ 
- Parent: indice (nell'array) del nodo padre di $i$

Vettore posizionale (per alberi d-ari (quasi) completi)

Vettore dei padri: un esempio

![[immagine122.png]]
![[immagine123.png]]

Vettore posizionale (per alberi d-ari completi)
- nodi arrangiati nell'array "per livelli"
- j-esimo figlio ($j \in {1,...,d}$) di i è in posizione $d(i-1)+j+1$
- il padre di i è in posizione $\lfloor (i-2)/d \rfloor +1$ 

![[immagine124.png]]
![[immagine125.png]]

## Rappresentazioni collegate di alberi

![[immagine126.png]]
![[immagine127.png]]

## Viste di alberi

Algoritmi che consentono l'accesso sistematico ai nodi e agli archi di un albero.
Gli algoritmi di vista si distinguono in base al particolare ordine di accesso ai nodi.

## Algoritmo di vista di profondità
### per alberi binari 

![[immagine128.png]]

L'algoritmo di vista in profondità (DFS) parte da r e procede visitando nodi di figlio in figlio fino a raggiungere una foglia. Retrocede poi al primo antenato che ha ancora figli non visitati (se esiste) e ripete il procedimento a partire da uno di quei figli.

![[immagine129.png]]
![[immagine130.png]]
![[immagine131.png]]
![[immagine132.png]]
![[immagine133.png]]
![[immagine134.png]]
![[immagine135.png]]
![[immagine136.png]]
![[immagine137.png]]
![[immagine138.png]]
![[immagine149.png]]
![[immagine139.png]]
![[immagine140.png]]
![[immagine141.png]]
![[immagine142.png]]
![[immagine143.png]]
![[immagine144.png]]
![[immagine145.png]]
![[immagine146.png]]
![[immagine147.png]]
![[immagine148.png]]
![[immagine149.png]]

## Complessità temporale

![[immagine150.png]]

## Algoritmo di vista in profondità
### versione ricorsiva (per alberi binari):

![[immagine151.png]]

*Vista in preordine*: radice, sottoalbero sin, sottoalbero destro.
*Vista simmetrica*: sottoalbero sin, radice, sottoalbero destro (scambia riga 2 con 3).
*Vista in postordine*: sottoalbero sin, sottoalbero destro, radice (sposta riga 2 dopo 4).

Esempi:
![[immagine152.png]]

## Algoritmo di vista in ampiezza
### versione iterativa(per alberi binari)

![[immagine153.png]]

L'algoritmo di vista in ampiezza (BFS) parte da r e procede visitando nodi per livelli successivi. Un nodo sul livello $i$ può essere visitato solo se tutti i nodi sul livello $i-1$ sono stati visitati.

![[immagine154.png]]
![[immagine155.png]]

## Complessità temporale

![[immagine157.png]]

## Utilizzo algoritmi di vista un esempio: calcolo dell'altezza

![[immagine158.png]]
![[immagine159.png]]
![[immagine160.png]]
![[immagine161.png]]

Esercizi alla fine del PDF: http://www.mat.uniroma2.it/~guala/cap3_2021.pdf
