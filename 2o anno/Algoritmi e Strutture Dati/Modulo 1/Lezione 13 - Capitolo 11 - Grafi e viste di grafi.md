## Definizione di grafo (non orientato)

Un grafo G = (V, E) consiste in:
- Un insieme V di vertici (o nodi);
- Un insieme E di coppie (non ordinate) di vertici, detti archi

![[immagine262.png]]

>Nota: E più probabilmente detto multigrafo, in quanto contiene archi paralleli

![[immagine263.png]]
![[immagine264.png]]

## Definizione di grafo diretto

Un grafo diretto D = (V, A) consiste in:
- Un insieme V di vertici (o nodi)
- Un insieme A di coppie ordinate di vertici detti archi diretti

![[immagine265.png]]
![[immagine266.png]]
![[immagine267.png]]

## Che relazione c'è fra grado dei nodi e numero di archi?

![[immagine268.png]]
![[immagine269.png]]

## Terminologia

![[immagine270.png]]

- Cammino: sequenza di nodi connessi da archi
- Lunghezza di un cammino: num archi del cammino
- Distanza : la lunghezza del più corto cammino tra due vertici si dice distanza tra i due vertici

	distanza fra L e A: 4
	in un grafo orientato, il cammino deve rispettare il verso di orientamento degli archi

![[immagine271.png]]

- G è connesso se esiste un cammino per ogni coppia di vertici
- Ciclo: un cammino chiuso, ovvero un cammino da un vertice a se stesso
- Il diametro è la massima distanza fra due nodi
	- $max_{u,v \in V}  \ dist(u, v)$ 
	- il diametro di un grafo non connesso è $\infty$ 

![[immagine272.png]]
![[immagine273.png]]

- Grafo pesato: è un grafo G = (V, E, w) in cui ad ogni arco viene associato un valore definito dalla funzione peso w (definita su un opportuno insieme, di solito i reali).

![[immagine274.png]]

## Quanti archi può avere un grafo di n nodi?

![[immagine275.png]]

## Come è fatto un grafo connesso con il minimo numero di archi?

>Definizione: Un albero è un grafo connesso ed aciclico.

![[immagine276.png]]
![[immagine277.png]]
![[immagine278.png]]

## Reti "delle dipendenze"

![[immagine279.png]]

nodi: compiti da svolgere
arco (u, v): u deve essere eseguito prima di v

esempi:
- esami e propedeucità
- moduli software di un progetto e dipendenze
- ...

>Problema: trovare un ordine in cui eseguire i compiti in modo da rispettare le dipendenze.

![[immagine280.png]]

![[immagine281.png]]

nodi: compiti da svolgere
arco(u, v): u e v non possono essere svolti insieme

Esempio:
- esami e vincoli
- certi esami non possono essere svolti lo stesso giorno (stesso anno, usano la stessa aula, ecc...)

![[immagine282.png]]
![[immagine283.png]]
![[immagine284.png]]
