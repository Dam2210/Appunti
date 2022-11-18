## I numeri di Fibonacci

### L'isola dei conigli

Leonardo da Pisa (Fibonacci) si interessò di molte cose tra cui il seguente problema di dinamica delle popolazioni:

>Quanto veloce si espanderebbe una popolazione di conigli sotto appropriate condizioni?

In particolare, partendo da una coppia di conigli in un'isola deserta, quante coppie si avrebbero nell'anno n?

### Le regole di riproduzione

- Una coppia di conigli concepisce due coniglietti di sesso diverso ogni anno, i quali formeranno una nuova coppia. 
- La gestazione dura un anno.
- I conigli cominciano a riprodursi soltanto al secondo anno dopo la loro nascita.
- I conigli sono immortali.

### L'albero dei conigli

La riproduzione dei conigli può essere descritta in un albero come segue:

![[immagine66.png]]

### La regola di espansione

- Nell'anno n, ci sono tutte le coppie dell'anno precedente, e una nuova coppia di conigli per ogni coppia di conigli per ogni coppia presente due anni prima
- Indicando con $F_n$ il numero di coppie dell'anno n, abbiamo la seguente relazione di ricorrenza:
$$F_n=\begin{cases}F_{n-1}+F_{n-2}&se\:n\geq 3\\1 &se\:n=1,2\end{cases}$$

### Il Problema

Primi numeri della sequenza di Fibonacci:
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, $F_{18} = 2584$, ...

Come calcoliamo $F_n$?

### Un approccio numerico

- Possiamo usare una funzione matematica che calcoli direttamente i numeri di Fibonacci.
- Si può dimostrare che:
$$F_n =\frac{1}{\sqrt 5}\ (\phi^n- \hat\phi^n)$$
dove:
$$
\begin{align}
& \phi = \frac{1 + \sqrt{5}}{2} \approx +1.618 \\
& \hat\phi = \frac{1-\sqrt{5}}{2} = -0.618
\end{align}
$$
### Algoritmo `fibonacci1`

algoritmo `fibonacci1`(intero n)$\rightarrow$ $intero$
	return $\frac{1}{\sqrt{5}}(\phi^n-\hat\phi^n)$ 

Correttezza?

- Qual'è l'accuratezza su $\phi$ e $\hat\phi$ per ottenere un risultato corretto?
- Ad esempio, con 3 cifre decimali:
$$\phi \approx 1.618\ e \ \hat\phi\approx-0.618$$
![[immagine67.png]]

###  Algoritmo `fibonacci2`

