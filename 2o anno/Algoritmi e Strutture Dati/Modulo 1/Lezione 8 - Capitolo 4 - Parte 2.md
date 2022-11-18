## Sommario

- Delimitazioni inferiori e superiori (di algoritmi e problemi)
- Quanto velocemente si possono ordinare $n$ elementi?
	- una soglia (asintotica) di velocità sotto la quale non si può scendere: un lower bound (per una classe di algoritmi ragionevoli - quelli basati su confronti).
	- una tecnica elegante che usa gli alberi di decisione.
- E se si esce da questa classe di algoritmi?
	- IntegerSort e BucketSort (per interi "piccoli").
	- RadixSort (per interi più "grandi").

## BucketSort

Per ordinare $n$ record con chiavi intere in $[1,k]$
- Esempio: ordinare $n$ record con campi:
	- nome, cognome, anno di nascita, matricola...
- Si potrebbe voler ordinare per matricola o per anno di nascita

Input del problema:
- $n$ record mantenuti in un array
- ogni elemento dell'array è un record con
	- campo chiave (rispetto al quale ordinare)
	- altri campi associati alla chiave (informazione satellite)

- Basta mantenere un array di liste, anzichè di contatori, ed operare come per IntegerSort
- La lista $Y[i]$ conterrà gli elementi con chiave uguale a $i$
- Concatenare poi le liste

>Tempo $O(n+k)$ come per IntegerSort

Esempio:
![[immagine101.png]]
![[immagine102.png]]
![[immagine103.png]]
![[immagine104.png]]
![[immagine105.png]]
![[immagine106.png]]
![[immagine107.png]]
![[immagine108.png]]
![[immagine109.png]]
![[immagine110.png]]
![[immagine111.png]]
![[immagine112.png]]
![[immagine113.png]]

- Un algoritmo è stabile se preserva l'ordine iniziale tra elementi con la stessa chiave
- domanda: il BucketSort è stabile?
- Il BucketSort è stabile se si appendono gli elementi di $X$ in coda alla opportuna lista $Y[i]$

## RadixSort

- Ordina $n$ interi con valori in $[1, k]$ 
- Rappresentiamo gli elementi in base b, ed eseguiamo una serie di BucketSort.
- Partiamo dalla cifra meno significativa verso quella più significativa:
	- Ordiniamo per l'i-esima cifra con una passata di BucketSort (stabile)
	- i-esima cifra è la chiave, il numero info satellite.

![[immagine114.png]]

Correttezza

- Se $x$ e $y$ hanno una diversa t-esima cifra, la t-esima passata di BucketSort li ordina
- Se $x$ e $y$ hanno la stessa t-esima cifra, la proprietà di stabilità del BucketSort li mantiene ordinati correttamente.

Dopo la t-esima passata di BucketSort, i numeri sono correttamente ordinati rispetto alle t cifre meno significative.

Tempo di esecuzione:
- $O(log_b \ k)$ passate di BucketSort
- Ciascuna passata richiede tempo $O(n+b)$
				$\downarrow$ 
			$O((n+b)log_b \ k)$ 

Se $b = \Theta(n)$ si ha $O(nlog_n \ k)=O( n \frac {logk}{logn})$ 
$\rightarrow$ Tempo lineare se $k = O(n^c)$, $c$ costante

ESERCIZIO SU PDF 6 (Capitolo 4: un lower bound al problema dell'ordinamento.)