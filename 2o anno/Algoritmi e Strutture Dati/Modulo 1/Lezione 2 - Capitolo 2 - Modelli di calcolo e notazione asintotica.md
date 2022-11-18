
## Un modello storico: la macchina di Turing

![[immagine68.png]]

## Un modello più realistico

- Macchina a registri (RAM: random access machine)
	- un programma finito
	- un mastro di ingresso e uno di uscita
	- una memoria strutturata come un array
		- ogni cella può contenere un qualunque valore intero/reale
	- due registri speciali: PC e ACC
- La RAM è un'astrazione dell'architettura di Von Neumann
![[immagine69.png]]

## Modello di calcolo: cosa posso fare

- L'analisi della complessità di un algoritmo è basata sul concetto di passo elementare
- Passi elementari su una RAM
	- istruzione ingresso/uscita (accesso nastri I/O)
	- operazione aritmetico/logica
	- accesso/modifica del contenuto della memoria

## Criterio di costo: quanto mi costa

- Criterio di costo uniforme:
	- tutte le operazioni hanno lo stesso costo
	- complessità temporale misuarata come numero di passi elementari eseguiti
- Criterio di costo logaritmico
	- Il costo di una operazione dipende dalla dimensione degli operandi dell'istruzione
	- Un'operazione su un operando di valore $x$ ha costo $logx$ 
	- E' un criterio di costo che modella meglio la complessità di algoritmi "numerici"

>Criterio di costo generalmente usato è quello uniforme.

## Caso peggiore, migliore e medio

- Misurare il tempo di esecuzione di un algoritmo in funzione della dimensione n delle istanze.
- Istanze diverse, a parità di dimensione, potrebbero però richiedere tempo diverso.
- Distinguiamo quindi ulteriormente tra analisi nel caso peggiore, migliore e medio.

## Caso peggiore

- Sia $tempo(I)$ il tempo di esecuzione di un algoritmo sull'istanza $I$
$$T_{worst}(n) = max_{istanze \ I\ di\ dimensione\ n}(tempo(I))$$
- Intuitivamente, $T_{worst}(n)$ è il tempo di esecuzione sulle istanze di ingresso che comportano più lavoro per l'algoritmo
- rappresenta una garanzia sul tempo di esecuzione di ogni istanza

## Caso migliore

- Sia $tempo(I)$ il tempo di esecuzione di un algoritmo sull'istanza $I$
$$T_{best}(n) = min_{istanze \ I\ di\ dimensione\ n}(tempo(I))$$
- Intuitivamente, $T_{best}(n)$ è il tempo di esecuzione sulle istanze di ingresso che comportano meno lavoro per l'algoritmo
- significa davvero qualcosa? (mah...)

## Caso medio

- Sia $P(I)$ la probabilità di occorenza dell'istanza $I$
$$T_{avg}(n) = \sum istanze\ I \ di\ dimensione\ n \ (P(I)tempo(I))$$
- Intuitivamente, $T_{avg}(n)$ è il tempo di esecuzione nel caso medio, ovvero sulle istanze di ingresso "tipiche" per il problema
- Come faccio a conoscere la distribuzione di probabilità sulle istanze?
- Semplice: (di solito) non posso conoscerla
- $\rightarrow$ faccio un'assunzione.
- Spesso è difficile fare assunzioni realistiche

# Una grande idea: notazione asintotica

## Notazione asintotica: intuizioni

Complessità computazionale di un algoritmo espressa con una funzione $T(n)$.

$T(n)$: # passi elementari eseguiti su una RAM nel caso peggiore di un'istanza di dimensione n.

Idea: descrivere $T(n)$ in modo qualitativo. Ovvero: perdere un po' in precisione (senza perdere l'essenziale) e guadagnare in semplicità.

$T(n)$: # passi elementari eseguiti su una RAM nel caso peggiore su un'istanza di dimensione n.

![[immagine70.png]]
![[immagine71.png]]
![[immagine72.png]]
![[immagine73.png]]

Esempi:
Sia $f(n) = 2n^2 + 3n$, allora
- $f(n) = O(n^3)$                (c =1, $n_0 = 3$) 
- $f(n) = O(n^2)$                (c = 3, $n_0 = 3$)
- $f(n)\neq O(n)$  

![[immagine74.png]]
![[immagine75.png]]
![[immagine76.png]]

Esempi:
Sia $f(n)=2n^2-3n$, allora
- $f(n) = \Omega(n)$                  (c = 1, $n_0 = 2$)
- $f(n)=\Omega(n^2)$                (c = 1, $n_0 = 3$)
- $f(n)\neq \Omega(n^3)$ 

![[immagine77.png]]
![[immagine78.png]]

## Notazione asintotica $\Theta$ 

![[immagine79.png]]

Esempi:
Sia $f(n) = 2n^2-3n$, allora
- $f(n) = \Theta(n^2)$                                        ($c_1=1, \ c_2 = 2, \ n_0 = 3$)
- $f(n)\neq \Theta(n)$
- $f(n)\neq \Theta(n^3)$ 

![[immagine80.png]]
![[immagine81.png]]
![[immagine82.png]]
![[immagine83.png]]
![[immagine84.png]]
![[immagine85.png]]
![[immagine86.png]]
![[immagine87.png]]
![[immagine88.png]]
![[immagine89.png]]
![[immagine90.png]]
![[immagine91.png]]

# Velocità asintotica di funzioni composte

## Velocità delle funzioni composte

Date $f(n)$ e $g(n)$
	La velocità ad andare a infinito della funzione $f(n)+g(n)$ è la velocità della più veloce tra $f(n)$ e $g(n)$.

Esempi:

$n^3+n = \Theta(n^3)$
$n + log^{10}\ n = \Theta(n)$

infatti: per ogni $n$

max{$f(n), \ g(n)$}$\leq f(n)+g(n)\leq$max{$f(n), \ g(n)$}$+$max{$f(n), \ g(n)$}
												$= 2$ max{$f(n), \ g(n)$}

Date $f(n)$ e $g(n)$:

La velocità ad andare a infinito della funzione $f(n)\ g(n)$ è la velocità  di $f(n)$ "più" la velocità di $g(n)$.

La velocità ad andare a infinito della funzione $f(n)/g(n)$ è la velocità di $f(n)$ "meno" la velocità di $g(n)$.

Esempio:

$$\frac{n^3log\ n+\sqrt nlog^3 \ n}{n^2+1} = \Theta(n \ logn)$$
![[immagine92.png]]
![[immagine93.png]]
![[immagine94.png]]
