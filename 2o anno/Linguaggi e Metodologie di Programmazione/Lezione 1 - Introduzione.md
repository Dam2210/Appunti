*Sito delle lezioni: http://art.uniroma2.it/teaching/lmp/part_I/

## Programmazione anni 60

Linguaggi di Programmazione già possedevano:
- Astrazione rispetto ai registri del processore
- Uso avanzato della memoria

Ma erano fortemente legati alle stesse modalità di organizzazione del flusso di operazioni.

il 'salto incondizionato' (GO TO, o, semplicemente, GOTO) rappresentava l'unico meccanismo per gestire il flusso decisionale di un algoritmo.

## Critiche al GOTO

Verso la fine degli anni 60, prime critiche alla programmazione tradizionale:

Esempio:
- Teorema di Böhm-Jacopini (1966): qualunque algoritmo può essere implementato utilizzando tre sole strutture, la sequenza, la selezione ed il ciclo (iterazione), da applicare ricorsivamente alla composizione di istruzioni elementari.

## Programmazione Strutturata

Un programma strutturato è composto da 3 combinazioni principali, applicate a blocchi primitivi di operazioni (statement).
- Sequenza: una esecuzione ordinata di statement.
- Selezione: a seconda dello 'stato' del programma, uno statement viene 'selezionato', da un insieme di statement per essere eseguito.
- Ciclo, o iterazione: uno statement è eseguito fino a che il programma non raggiunge un determinato stato.

![[immagine1.png]]
*NOTA: in blu, le rappresentazioni originariamente utilizzate per rappresentare i tre elementi fondamentali della programmazione strutturata: la sequenza, la selezione, la iterazione.

I seguenti requisiti devono essere rispettati da un linguaggio di programmzione strutturato.
- Completezza: le tre strutture della programmazione strutturata devono avere almeno una rappresentazione sintattica nel linguaggio (e opzionalmente, delle variazioni). 
- Singolo punto di Ingresso e Uscita: in ogni struttura di controllo si devono poter identificare un singolo punto di ingresso e un singolo punto di uscita. Ciò è necessario per la succesiva...
- Componibilità:  ogni struttura di controllo deve poter essere considerata come una macro-statement, in modo da poter essere usata, ricorsivamente, come istruzione in altre strutture di controllo.

## Programmazione Procedurale

Consiste nella possibilità di agevolare la leggibilità di un programma (e la sua manutenibilità) tramite la definizione di blocchi di codice, racchiusi da delimitatori e usualmente identificati da un nome.

Tali blocchi assumono il nome di:
- Subroutine (in italiano sottoprogrammi)
- Procedure
- Funzioni
- Metodi
*Tali nomi implicano differenze dipendenti dal contesto del modello di linguaggio usato.

## Programmazione Orientata agli Oggetti

### Principi Fondamentali dell'OOP (Object Oriented Programming)
- Encapsulation (Incapsulamento):
	- Nascondere dettagli implementativi, permettendo di raggiungere solo alcune informazioni tramite accessors e mutators.
- Abstraction (Astrazione):
	- Direttamente correlata alla precedente.
	- la Abstraction ha a che fare con la definizione di modelli, viste ecc...  per gli oggetti che si vogliono rappresentare.
	- ...mentre la Encapsulation garantisce che le implementazioni di tali modelli rimangono opache ai loro utilizzatori.
- Inheritance (Ereditarietà):
	- La Ereditarietà permette di raccogliere a fattor comune caratteristiche condivise da oggetti simili, definendo dei modelli che rappresentano tali caratteristiche, e specializzando tali modelli per insiemi di oggetti via via più ristretti, ma accomunati ad una similiarità maggiore (ossia, più caratteristiche comuni).
	- Esempio: la classe delle autovetture accomuna tutti gli oggetti con 3 o 4 ruote dotate di qualche sistema di propulsione e che permettono a delle persone di spostarsi. La classe delle citycar può essere definita come una specializzazione della precedente (quindi eredita dalla precedente) perchè comprende tutte le sue caratteristiche ed ha in più caratteristiche aggiuntive, o restrizioni su quelle già definite (e.g. avere dimensioni ridotte, o bassi consumi etc...)
- Polymorphism (Polimorfismo):
	- Overriding (run-time polymorphism)
	- Overloading (compile-time polymorphism)