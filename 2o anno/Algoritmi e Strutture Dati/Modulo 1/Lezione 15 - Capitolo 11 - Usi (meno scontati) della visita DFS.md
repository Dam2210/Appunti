## Informazioni utili: tenere il tempo

![[immagine301.png]]
![[immagine302.png]]
![[immagine303.png]]
![[immagine304.png]]
![[immagine305.png]]

## Cicli, DAG e ordinamenti topologici
### riconoscere la presenza di un ciclo in un grafo diretto

>[!info]- Algoritmo:
>Fai una visita DFS e controlla se c'è un arco all'indietro.

>[!important]- Proprietà:
>Un grafo diretto G ha un ciclo se e solo se la visita DFS rivela un arco all'indietro.

($\xLeftarrow[]{}$): se c'è arco all'indietro, chiaramente G ha un ciclo
($\xRightarrow[]{}$): se c'è ciclo $<v_0,v_1,...,v_k=v_0>$
sia $v_i$ è il primo nodo scoperto nella visita
$v_i$ termina la visita dopo che $v_{i+1}$ ha terminato la sua
$v_{i+1}$ termina la visita dopo che $v_{i+2}$ ha terminato la sua
.
.
.
Quindi, per transitività, $v_i$ termina la visita dopo che $v_{i-1}$ ha terminato la sua
allora $(v_{i-1}, v_i)$ è un arco all'inditro.

![[immagine306.png]]

>[!important]- Definizione:
>Un grafo diretto aciclico (DAG) è un grafo diretto G che non contiene cicli (diretti).

>[!important]- Definizione:
>Un ordinamento topologico di un grafo diretto G = (V, E) è una finzione biettiva $\sigma:V\to\{1,2,...,n\}$ tale che per ogni arco $(u, v)\in E$, $\sigma(u)<\sigma(v)$       

![[immagine307.png]]
![[immagine308.png]]

Quali grafi (diretti) ammettono un ordinamento topologico?

>[!important]- Teorema:
>Un grafo G ammette un ordinamento topologico se e solo se G è un DAG.

Dim:
($\xRightarrow[]{}$) 

per suurdo: sia $\sigma$ un ordinamento topologico di G
e sia $<v_0, v_1,...,v_k=v_0>$ un ciclo
allora $\sigma(v_0)<\sigma(v1)<...<\sigma(v_{k-1})<\sigma(v_k)=\sigma(v_0)$ 

($\xLeftarrow[]{}$): ... adesso siamo un algoritmo costruttivo.

![[immagine309.png]]
![[immagine310.png]]
![[immagine311.png]]
![[immagine312.png]]

[Esempio: Ordinamento Topologico](http://www.mat.uniroma2.it/~guala/usi_dfs_2021.pdf#page=17) 

## Componenti fortemente connesse

Una componente fortemente connessa di un grafo G = (V, E) è un insieme massimale di vertici $C\subseteq V$ tale che per ogni coppia di nodi $u$ e $v$ in $C$, $u$ è raggiungibile da $v$ e $v$ è raggiungibile da $u$.

massimale: se si aggiunge un qualsiasi vertice a $C$ la proprietà non è più vera.

il grafo delle componenti fortemente connesse di G è sempre un DAG

![[immagine313.png]]
![[immagine314.png]]

Come si possono calcolare le componenti fortemente connesse di un grafo diretto?

>[!important]- Proprietà 1:
>Se si esegue la procedura visitaDFSricorsiva a partire da un nodo $u$ la procedura termina dopo che tutti i nodi raggiungibili da $u$ sono stati visistati.

>[!important]- Idea:
>Eseguire una visita a partire da un nodi di una componente pozzo, "eliminare" la componente e ripetere.

![[immagine313.png]]
![[immagine314.png]]

Come trovo una componente pozzo?

>[!important]- Proprietà 2:
>Se $C$ e $C'$ sono due componenti e c'è un arco da un nodo in $C$ verso uno in $C'$, allora il più grande valore $post()$ in $C$ è maggiore del più alto valore di $post()$ di $C'$.
>dim: se la DFS visita prima $C'$ di $C$: banale.
>se visita prima $C$, allora si ferma dopo che ha raggiunto tutti i nodi di $C$ e $C'$ e termina su un nodo di $C$

>[!important]- Proprietà 3:
>Il nodo che riceve una visita DFS il valore più grande di $post()$ appartiene a una componente sorgente

ma avevamo bisogno di una componente pozzo?

IDEA: invertiamo gli archi.

![[immagine315.png]]
![[immagine314.png]]
![[immagine316.png]]
![[immagine317.png]]
![[immagine318.png]]
![[immagine319.png]]
