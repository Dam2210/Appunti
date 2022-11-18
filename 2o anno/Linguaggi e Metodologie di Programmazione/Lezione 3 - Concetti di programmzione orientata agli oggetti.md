
### Che cos'è un'oggetto?

Un oggettomè un pacchetto software di stato e comportamento correlati. Gli oggetti software sono spesso usati per modellare gli oggetti del mondo reale che trovi nella vita di tutti i giorni. Questa lezione spiega come lo stato e il comportamento sono rappresentati all'interno di un oggetto, introdice il concetto di incapsulamento dei dati e spiega i vantaggi della progettazione del software in questo modo.

### Che cos'è una classe?

Una classe è un progetto o un prototipo da cui vengono creati gli oggetti. Questa sezione definisce una classe che modella lo stato e il comportamento di un oggetto nel mondo reale. Si concentra intenzionalmente sulle basi, mostrando come anche una classe semplice può modellare in modo pulito stato e comportamento.

### Che cos'è l'eredita?

L'ereditarietà fornisce un meccanismo potente e naturale per organizzare e strutturare il software. Questa sezione spiega come le classi ereditano lo stato e il comportamento dalle loro superclassi e spiega come derivare una classe da un'altra usando la semplice sintassi fornita dal linguaggio di programmazione Java.

### Che cos'è un'interfaccia?

Un'interfaccia è un contratto tra una classe e il mondo esterno. Quando una classe implementa un'interfaccia, promette di fornire il comportamento pubblicato da quell'interfaccia. Questa sezione definisce un'interfaccia semplice e spiega le modifiche necessarie per qualsiasi classe che la implementa.

### Che cos'è un pacchetto?

Un pacchetto è uno spazio dei nomi per organizzare classi e interfaccie in modo logico. L'inserimento del codice nei pacchetti semplifica la gestione di progetti software di grandi dimensioni. Questa sezione spiega perchè è utile e introduce l'Application Programming Interface (API) fornita dalla piattaforma Java.

-----------------------------------------------------------------------

## Che cos'è un oggetto?

Gli oggetti sono fondamentali per comprendere la tecnologia orientata agli oggetti. 
Gli oggetti nel mondo reale condividono due caratteristiche: hanno tutti uno stato e un comportamento. I cani hanno stato (nome, colore, razza, fame) e comportamento (abbaiare, andare a prendere, scodinzolare). Identificare lo stato e il comportamento degli oggetti del mondo reale è un ottimo modo per iniziare a pensare in termini di programmazione orientata agli oggetti.

![[immagine31.png]]

Gli oggetti software sono concettualmente simili agli oggetti del mondo reale: anch'essi sono costituiti da stato e comportamento correlato. Un oggetto memorizza il suo stato in campi (variabili in alcuni linguaggi di programmazione) ed espone il suo comportamento attraverso metodi (funzioni in alcuni linguaggi di programmazione). I metodi operano sullo stato interno di un oggetto e fungono da meccanismo principale per la comunicazione da oggetto a oggetto. Nascondere lo stato interno e richiedere che tutte le interazioni vengano eseguite attraverso i metodi di un oggetto è noto come incapsulamento dei dati, un principio fondamentale della programmazione orientata agli oggetti.

Consideriamo una bicicletta, ad esempio:

![[immagine32.png]]

Attribuendo lo stato (velocità attuale, cadenza attuale del pedale e marcia attuale) e fornendo metodi per modificare tale stato, l'oggetto mantiene il controllo su come il mondo esterno può usarlo. Ad esempio, se la bicicletta ha solo 6 marce, un metodo per cambiare marcia potrebbe rifiutare qualsiasi valore inferiore a 1 o meggiore di 6.

Il raggruppamento del codice in singoli oggetti software offre numerosi vantaggi, tra cui:

1. Modularità: il codice sorgente di un oggetto può essere scritto e mantenuto indipendentemente dal codice sorgente di altri oggetti. Una volta creato, un oggetto può essere facilmente passato all'interno del sistema.
2. Nascondere le informazioni: interagendo solo con i metodi di oggetto, i dettagli della sua implementazione interna rimangono nascosti al mondo esterno.
3. Riutilizzo del codice: se un oggetto esiste già (forse scritto da un altro sviluppatore di software), puoi utilizzare quell'oggetto nel tuo programma. Ciò consente agli specialisti di implementare/testare/debug di oggetti complessi e specifici per attività. 
4. Facilità di inserimento e debugging: se un oggetto risulta problematico, puoi semplicemente rimuoverlo dall'applicazione e collegare un oggetto diverso come sostituto.

-----------------------------------------------------------------------

## Che cos'è una classe?

Nella realtà, esistono molti singoli oggetti tutti dello stesso tipo. Potrebbero esistere migliaia di altre biciclette, tutte della stessa marca e modello. Ogni bicicletta è stata costruita dalla stessa serie di progetti e quindi contiene gli stessi componenti. In termini orientati agli oggetti, diciamo che la bicicletta è un'istanza della classe di oggetti nota come biciclette. Una classe è il progetto da cui vengono creati i singoli oggetti.

La $Bycicle \ class$ seguente è una possibile implementazione di una bicicletta:

classe Bicicletta {

	int cadence = 0;
	int speed = 0;
	int gear = 1;
	
	void changeCadence(int newValue) {
		cadence = newValue;
	}
	
	void changeGear(int newValue) {
		gear = newValue;
	}
	
	void speedUp(int increment) {
		speed = speed + increment;
	}
	
	void applyBrakes(int decrement) {
		speed = speed - decrement;
	}
	
	void printStates() {
		System.out.println("cadence:" + cadence + "speed:" + speed +
		"gear:" + gear);
	}
}

La sintassi del linguaggio Java sembrerà nuova, ma il design di questa classe si basa sulla discussione precedente sugli oggetti bicicletta. I campi $cadence, \  speed,$  e $\  gear$ rappresentano lo stato dell'oggetto e i metodi ($changeCadence, \ changeGear, \ speedUp$ ecc.) ne definiscono l'interazione con il mondo esterno.

Potresti aver notato che la Bicycleclass non contiene un metodo main . Questo perchè non è un'applicazione completa; è solo il progetto per le biciclette che potrebbe essere utilizzato in un'applicazione. La responsabilità di creare e utilizzare nuovi Bicycle oggetti appartiene a qualche altra classe nell'applicazione.

Ecco una BicycleDemo class che crea due Bicycle oggetti separati e invoca i loro metodi:

class BicycleDemo{

	public static void main(String[] args) {
			//crea due diversi
			//oggetti per biciclette
			Bicycle bike1 = new Bicycle();
			Bicycle bike2 = new Bicycle();
			
			//invoca metodi su
			//questi oggetti
			bike1.changeCadence(50);
			bike1.speedUp(10);
			bike1.changeGear(2);
			bike1.printStates();
			
			bike2.changeCadence(50);
			bike2.speedUp(10);
			bike2.changeGear(2);
			bike2.changeCadence(40);
			bike2.speedUp(10);
			bike2.changeGear(3);
			bike2.printStates();
	}
}

>L'output di questo test stampa la cadenza del pedale finale, la velocità e la marcia per le due biciclette:
>
>cadence: 50, speed: 10, gear: 2
>cadence: 40, speed: 20, gear: 3

----

## Che cos'è l'ereditarietà?

Diversi tipi di oggetti hanno spesso una certa quantità in comune tra loro. Mountain bike, bici da strada e bici tandem, ad esempio, condividono tutte le caratteristiche delle biciclette (velocità attuale, cadenza del pedale attuale, marcia attuale). Eppure ognuno definisce anche caratteristiche aggiuntive che li rendono diversi: le biciclette tandem hanno due sedili e due set di manubri; le bici da strada hanno il manubrio drop; alcune mountain bike hanno una corona aggiuntiva, che conferisce loro un rapporto di trasmissione inferiore.

La programmazione orientata agli oggetti consente alle classi di _ereditare_ lo stato e il comportamento comunemente usati da altre classi. In questo esempio, Bicycle ora diventa la superclasse di `MountainBike`, `RoadBike`, `TandemBike`. Nel linguaggio di programmazione Java, ogni classe può avere una superclasse diretta e ogni superclasse ha il potenziale per un numero illimitato di _sottoclassi_:

![[immagine65.png]]

La sintassi per creare una sottoclasse è semplice. All'inizio della tua dichiarazione di classe, usa la $extends$ parola chiave, seguita dal nome della classe da cui ereditare:

class MountainBike **extends** Bicycle {

    // new fields and methods defining 
    // a mountain bike would go here

}

Ciò fornisce `MountainBike` tutti gli stessi campi e metodi di `Bicycle`, ma consente al suo codice di concentrarsi esclusivamente sulle caratteristiche che lo rendono unico. Questo rende il codice per le tue sottoclassi facile da leggere. Tuttavia, devi fare attenzione a documentare correttamente lo stato e il comportamento definiti da ciascuna superclasse, poiché quel codice non apparirà nel file sorgente di ciascuna sottoclasse.

-----

## Cos'è un'interfaccia?

Come hai già imparato, gli oggetti definiscono la loro interazione con il mondo esterno attraverso i metodi che espongono. I metodi costituiscono l'_interfaccia_ dell'oggetto con il mondo esterno; i pulsanti sulla parte anteriore del televisore, ad esempio, sono l'interfaccia tra te e il cablaggio elettrico sull'altro lato del suo involucro di plastica. Premi il pulsante "power" per accendere e spegnere il televisore.

Nella sua forma più comune, un'interfaccia è un gruppo di metodi correlati con corpi vuoti. Il comportamento di una bicicletta, se specificato come interfaccia, potrebbe apparire come segue:

interface Bicycle {

    //  wheel revolutions per minute
    void changeCadence(int newValue);

    void changeGear(int newValue);

    void speedUp(int increment);

    void applyBrakes(int decrement);
}

Per implementare questa interfaccia, il nome della tua classe cambierebbe (in una particolare marca di bicicletta, ad esempio, come `ACMEBicycle`) e useresti la `implements`parola chiave nella dichiarazione della classe:

class ACMEBicycle **implements** Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;

   // The compiler will now require that methods
   // changeCadence, changeGear, speedUp, and applyBrakes
   // all be implemented. Compilation will fail if those
   // methods are missing from this class.

    void changeCadence(int newValue) {
         cadence = newValue;
    }

    void changeGear(int newValue) {
         gear = newValue;
    }

    void speedUp(int increment) {
         speed = speed + increment;   
    }

    void applyBrakes(int decrement) {
         speed = speed - decrement;
    }

    void printStates() {
         System.out.println("cadence:" +
             cadence + " speed:" + 
             speed + " gear:" + gear);
    }
}

L'implementazione di un'interfaccia consente a una classe di diventare più formale sul comportamento che promette di fornire. Le interfacce formano un contratto tra la classe e il mondo esterno e questo contratto viene applicato in fase di compilazione dal compilatore. Se la tua classe afferma di implementare un'interfaccia, tutti i metodi definiti da tale interfaccia devono apparire nel codice sorgente prima che la classe venga compilata correttamente.

>**Nota:**  per compilare effettivamente la `ACMEBicycle`classe, dovrai aggiungere la `public`parola chiave all'inizio dei metodi di interfaccia implementati.

------

## Cos'è un pacchetto?

Un pacchetto è uno spazio dei nomi che organizza un insieme di classi e interfacce correlate. Concettualmente puoi pensare ai pacchetti come simili a diverse cartelle sul tuo computer. È possibile mantenere le pagine HTML in una cartella, le immagini in un'altra e gli script o le applicazioni in un'altra ancora. Poiché il software scritto nel linguaggio di programmazione Java può essere composto da centinaia o _migliaia_ di classi singole, ha senso mantenere le cose organizzate inserendo classi e interfacce correlate in pacchetti.

La piattaforma Java fornisce un'enorme libreria di classi (un insieme di pacchetti) adatta per l'uso nelle proprie applicazioni. Questa libreria è nota come "Application Programming Interface" o "API" in breve. I suoi pacchetti rappresentano le attività più comunemente associate alla programmazione generica. Ad esempio, un `String`oggetto contiene stato e comportamento per le stringhe di caratteri; un `File` oggetto consente a un programmatore di creare, eliminare, ispezionare, confrontare o modificare facilmente un file sul filesystem; un`Socket`l'oggetto consente la creazione e l'utilizzo di socket di rete; vari oggetti della GUI controllano pulsanti e caselle di controllo e qualsiasi altra cosa relativa alle interfacce utente grafiche. Ci sono letteralmente migliaia di classi tra cui scegliere. Ciò consente a te, programmatore, di concentrarti sulla progettazione della tua particolare applicazione, piuttosto che sull'infrastruttura necessaria per farla funzionare.
