## Classi

Ecco un codice di esempio per una possibile implementazione di una `Bicycle` class, per darti una panoramica di una dichiarazione di classe:

public class Bicycle {
        
    // **the Bicycle class has**
    // **three _fields_**
    public int cadence;
    public int gear;
    public int speed;
        
    // **the Bicycle class has**
    // **one _constructor_**
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
        
    // **the Bicycle class has**
    // **four _methods_**
    public void setCadence(int newValue) {
        cadence = newValue;
    }
        
    public void setGear(int newValue) {
        gear = newValue;
    }
        
    public void applyBrake(int decrement) {
        speed -= decrement;
    }
        
    public void speedUp(int increment) {
        speed += increment;
    }
        
}

Una dichiarazione di classe per una `MountainBike` class che è una sottoclasse di `Bicycle`potrebbe assomigliare a questa:

public class MountainBike extends Bicycle {
        
    // **the MountainBike subclass has**
    // **one _field_**
    public int seatHeight;

    // **the MountainBike subclass has**
    // **one _constructor_**
    public MountainBike(int startHeight, int startCadence,
                        int startSpeed, int startGear) {
        super(startCadence, startSpeed, startGear);
        seatHeight = startHeight;
    }   
        
    // **the MountainBike subclass has**
    // **one _method_**
    public void setHeight(int newValue) {
        seatHeight = newValue;
    }   

}

`MountainBike` eredita tutti i campi e i metodi `Bicycle` e aggiunge il campo `seatHeight` e un metodo per impostarlo (le mountain bike hanno i sedili che possono essere spostati su e giù come richiesto dal terreno).

## Dichiarare la classe

Hai visto classi definite nel modo seguente:

classe _MyClass_ {
    // campo, costruttore e
    // dichiarazioni di metodo
}

Questa è una _dichiarazione di classe_ . Il _corpo della classe_ (l'area tra le parentesi graffe) contiene tutto il codice che prevede il ciclo di vita degli oggetti creati dalla classe: costruttori per inizializzare nuovi oggetti, dichiarazioni per i campi che forniscono lo stato della classe e dei suoi oggetti, e metodi per implementare il comportamento della classe e dei suoi oggetti.

La precedente dichiarazione di classe è minima. Contiene solo quei componenti di una dichiarazione di classe che sono richiesti. Puoi fornire maggiori informazioni sulla classe, come il nome della sua superclasse, se implementa interfacce e così via, all'inizio della dichiarazione di classe. Per esempio:

class _MyClass extends MySuperClass implements YourInterface_ {
    // field, constructor, and
    // method declarations
}

significa che `MyClass` è una sottoclasse di `MySuperClass` e che implementa l'`YourInterface` interfaccia.

Puoi anche aggiungere modificatori come _public_ o _private_ all'inizio, così puoi vedere che la riga di apertura di una dichiarazione di classe può diventare piuttosto complicata. I modificatori _public_ e _private_ , che determinano a cosa possono accedere le altre classi `MyClass`, verranno discussi più avanti in questa lezione. La lezione sulle interfacce e sull'ereditarietà spiegherà come e perché dovresti usare le parole chiave _extends_ e _implements_ in una dichiarazione di classe. 

In generale, le dichiarazioni di classe possono includere questi componenti, nell'ordine:

1.  Modificatori come _public_ , _private_ e molti altri che incontrerai in seguito. (Tuttavia, tieni presente che il modificatore _privato_ può essere applicato solo alle classi nidificate.)
2.  Il nome della classe, con la lettera iniziale maiuscola per convenzione.
3.  Il nome del genitore della classe (superclasse), se presente, preceduto dalla parola chiave _extends_ . Una classe può _estendere_ (sottoclasse) solo un genitore.
4.  Un elenco separato da virgole di interfacce implementate dalla classe, se presente, preceduto dalla parola chiave _implements_ . Una classe può _implementare_ più di un'interfaccia.
5.  Il corpo della classe, racchiuso tra parentesi graffe ( {} ).

## Dichiarazione delle variabili membro

Esistono diversi tipi di variabili:

-   Variabili membro in una classe: queste sono chiamate _campi_ .
-   Variabili in un metodo o blocco di codice: queste sono chiamate _variabili locali_ .
-   Variabili nelle dichiarazioni di metodo: queste sono chiamate _parametri_ .

La `Bicycle` classe utilizza le seguenti righe di codice per definire i propri campi:

public int cadence;
public int gear;
public int speed;

Le dichiarazioni di campo sono composte da tre componenti, nell'ordine:

1.  Zero o più modificatori, come `public` o `private`.
2.  Il tipo del campo.
3.  Il nome del campo.

I campi di `Bicycle` sono denominati `cadence`, `gear`, e `speed` e sono tutti di tipo dati intero (`int`). La `public` parola chiave identifica questi campi come membri pubblici, accessibili da qualsiasi oggetto che può accedere alla classe.

## Modificatori d'accesso

Il primo modificatore (più a sinistra) utilizzato consente di controllare quali altre classi hanno accesso a un campo membro. Per il momento, considera solo `public` e `private.`Altri modificatori di accesso verranno discussi in seguito.

-   `public` modificatore: il campo è accessibile da tutte le classi.
-   `private` modificatore: il campo è accessibile solo all'interno della propria classe.

Nello spirito dell'incapsulamento, è comune rendere privati i campi. Ciò significa che è possibile accedervi _direttamente_ solo dalla classe Bicycle. Tuttavia, abbiamo ancora bisogno di accedere a questi valori. Questo può essere fatto _indirettamente_ aggiungendo metodi pubblici che ottengono i valori di campo per noi:

public class Bicycle {
        
    private int cadence;
    private int gear;
    private int speed;
        
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
        
    public int getCadence() {
        return cadence;
    }
        
    public void setCadence(int newValue) {
        cadence = newValue;
    }
        
    public int getGear() {
        return gear;
    }
        
    public void setGear(int newValue) {
        gear = newValue;
    }
        
    public int getSpeed() {
        return speed;
    }
        
    public void applyBrake(int decrement) {
        speed -= decrement;
    }
        
    public void speedUp(int increment) {
        speed += increment;
    }
}

## Tipi

Tutte le variabili devono avere un tipo. Puoi usare tipi primitivi come `int`, `float`, `boolean`, ecc. Oppure puoi usare tipi di riferimento, come stringhe, array o oggetti.

## Nomi variabili

In questa lezione, tieni presente che le stesse regole e convenzioni di denominazione vengono utilizzate per i nomi dei metodi e delle classi, tranne questi:

-   la prima lettera del nome di una classe dovrebbe essere in maiuscolo, e
-   la prima (o l'unica) parola nel nome di un metodo dovrebbe essere un verbo.

## Definire i metodi

Ecco un esempio di una tipica dichiarazione di metodo:

public double calculateAnswer(double wingSpan, int numberOfEngines,
                              double length, double grossTons) {
    //do the calculation here
}

Gli unici elementi richiesti di una dichiarazione di metodo sono il tipo restituito, il nome, una coppia di parentesi `()`e un corpo tra parentesi graffe, `{}`.

Più in generale, le dichiarazioni di metodo hanno sei componenti, nell'ordine:

1.  Modificatori, come `public`, `private`, e altri di cui imparerai in seguito.
2.  Il tipo restituito: il tipo di dati del valore restituito dal metodo o `void`se il metodo non restituisce un valore.
3.  Il nome del metodo: le regole per i nomi dei campi si applicano anche ai nomi dei metodi, ma la convenzione è leggermente diversa.
4.  L'elenco dei parametri tra parentesi: un elenco delimitato da virgole di parametri di input, preceduto dai relativi tipi di dati, racchiuso tra parentesi, `()`. Se non ci sono parametri, è necessario utilizzare parentesi vuote.
5.  Un elenco di eccezioni, di cui parleremo più avanti.
6.  Il corpo del metodo, racchiuso tra parentesi graffe: il codice del metodo, inclusa la dichiarazione delle variabili locali, va qui.

>**Definizione:**  due dei componenti di una dichiarazione di metodo comprendono la _firma_ del metodo: il nome del metodo ei tipi di parametro.

La firma del metodo sopra dichiarato è:

calculateAnswer(double, int, double, double)

## Dare un nome a un metodo

Sebbene un nome di metodo possa essere qualsiasi identificatore legale, le convenzioni di codice limitano i nomi di metodo. Per convenzione, i nomi dei metodi dovrebbero essere un verbo in minuscolo o un nome composto da più parole che inizia con un verbo in minuscolo, seguito da aggettivi, nomi, ecc. Nei nomi composti da più parole, la prima lettera di ciascuna delle seconde parole e le seguenti dovrebbe essere in maiuscolo. Ecco alcuni esempi:

run
runFast
getBackground
getFinalData
compareTo
setX
isEmpty

In genere, un metodo ha un nome univoco all'interno della sua classe. Tuttavia, un metodo potrebbe avere lo stesso nome di altri metodi a causa _dell'overloading del metodo_ .

Il linguaggio di programmazione Java supporta l' _overloading_ dei metodi e Java può distinguere tra metodi con diverse _firme di metodo_ . Ciò significa che i metodi all'interno di una classe possono avere lo stesso nome se hanno elenchi di parametri diversi.

Si supponga di avere una classe in grado di utilizzare la calligrafia per disegnare vari tipi di dati (stringhe, numeri interi e così via) e che contenga un metodo per disegnare ogni tipo di dati. È complicato utilizzare un nuovo nome per ogni metodo, ad esempio `drawString,` `drawInteger, drawFloat` e così via. Nel linguaggio di programmazione Java è possibile utilizzare lo stesso nome per tutti i metodi di disegno ma passare un elenco di argomenti diverso a ciascun metodo. Pertanto, la classe di disegno dati potrebbe dichiarare quattro metodi denominati `draw`, ognuno dei quali ha un elenco di parametri diverso.

public class DataArtist {
    ...
    public void draw(String s) {
        ...
    }
    public void draw(int i) {
        ...
    }
    public void draw(double f) {
        ...
    }
    public void draw(int i, double f) {
        ...
    }
}

I metodi sovraccaricati si differenziano per il numero e il tipo degli argomenti passati nel metodo. Nell'esempio di codice, `draw(String s)`e `draw(int i)`sono metodi distinti e univoci perché richiedono tipi di argomenti diversi.

Non puoi dichiarare più di un metodo con lo stesso nome e lo stesso numero e tipo di argomenti, perché il compilatore non può distinguerli.

Il compilatore non considera il tipo restituito durante la differenziazione dei metodi, quindi non è possibile dichiarare due metodi con la stessa firma anche se hanno un tipo restituito diverso.

>**Nota:**  i metodi sovraccaricati dovrebbero essere usati con parsimonia, poiché possono rendere il codice molto meno leggibile.

# Fornire costruttori per le tue classi

Una classe contiene costruttori che vengono invocati per creare oggetti dal progetto della classe. Le dichiarazioni del costruttore sembrano dichiarazioni di metodo, tranne per il fatto che usano il nome della classe e non hanno un tipo restituito. Ad esempio, `Bicycle` ha un costruttore:

public Bicycle(int startCadence, int startSpeed, int startGear) {
    gear = startGear;
    cadence = startCadence;
    speed = startSpeed;
}

Per creare un nuovo `Bicycle` oggetto chiamato `myBike`, un costruttore viene chiamato `new` dall'operatore:

Bicycle myBike = new Bicycle(30, 0, 8);

`new Bicycle(30, 0, 8)` crea spazio in memoria per l'oggetto e ne inizializza i campi.

Sebbene `Bicycle` abbia un solo costruttore, potrebbe averne altri, incluso un costruttore senza argomenti:

public Bicycle() {
    gear = 1;
    cadence = 10;
    speed = 0;
}

`Bicycle yourBike = new Bicycle();` richiama il costruttore no-argument per creare un nuovo `Bicycle` oggetto chiamato `yourBike`.

Entrambi i costruttori avrebbero potuto essere dichiarati `Bicycle` perché hanno elenchi di argomenti diversi. Come per i metodi, la piattaforma Java differenzia i costruttori in base al numero di argomenti nell'elenco e ai loro tipi. Non puoi scrivere due costruttori che hanno lo stesso numero e tipo di argomenti per la stessa classe, perché la piattaforma non sarebbe in grado di distinguerli. Ciò provoca un errore in fase di compilazione.

Non devi fornire alcun costruttore per la tua classe, ma devi stare attento quando lo fai. Il compilatore fornisce automaticamente un costruttore predefinito senza argomenti per qualsiasi classe senza costruttori. Questo costruttore predefinito chiamerà il costruttore senza argomenti della superclasse. In questa situazione, il compilatore si lamenterà se la superclasse non ha un costruttore senza argomenti, quindi è necessario verificare che lo sia. Se la tua classe non ha una superclasse esplicita, allora ha una superclasse implicita di `Object`, che _ha_ un costruttore senza argomenti.

Puoi usare tu stesso un costruttore di superclassi. La `MountainBike`classe all'inizio di questa lezione ha fatto proprio questo. Questo sarà discusso più avanti, nella lezione sulle interfacce e l'ereditarietà.

È possibile utilizzare i modificatori di accesso nella dichiarazione di un costruttore per controllare quali altre classi possono chiamare il costruttore.

>**Nota:** se un'altra classe non può chiamare un `MyClass` costruttore, non può creare direttamente `MyClass` oggetti.

# Passare informazioni a un metodo oa un costruttore

La dichiarazione per un metodo o un costruttore dichiara il numero e il tipo degli argomenti per quel metodo o costruttore. Ad esempio, il seguente è un metodo che calcola le rate mensili di un mutuo per la casa, in base all'importo del prestito, al tasso di interesse, alla durata del prestito (il numero di periodi) e al valore futuro del prestito:

public double computePayment(
                  double **loanAmt**,
                  double **rate**,
                  double **futureValue**,
                  int **numPeriods**) {
    double interest = **rate** / 100.0;
    double partial1 = Math.pow((1 + interest), 
                    - **numPeriods**);
    double denominator = (1 - partial1) / interest;
    double answer = (-**loanAmt** / denominator)
                    - ((**futureValue** * partial1) / denominator);
    return answer;
}

Questo metodo ha quattro parametri: l'importo del prestito, il tasso di interesse, il valore futuro e il numero di periodi. I primi tre sono numeri in virgola mobile a precisione doppia e il quarto è un numero intero. I parametri vengono utilizzati nel corpo del metodo e in fase di esecuzione assumeranno i valori degli argomenti passati.

>**Nota**: i _parametri_ si riferiscono all'elenco di variabili in una dichiarazione di metodo. _Gli argomenti_ sono i valori effettivi che vengono passati quando viene richiamato il metodo. Quando si richiama un metodo, gli argomenti utilizzati devono corrispondere ai parametri della dichiarazione nel tipo e nell'ordine.

## Tipi di parametri

È possibile utilizzare qualsiasi tipo di dati per un parametro di un metodo o un costruttore. Ciò include tipi di dati primitivi, come double, float e interi, come hai visto nel `computePayment` metodo, e tipi di dati di riferimento, come oggetti e matrici.

Ecco un esempio di metodo che accetta un array come argomento. In questo esempio, il metodo crea un nuovo `Polygon` oggetto e lo inizializza da una matrice di `Point` oggetti (supponiamo che `Point` sia una classe che rappresenta una coordinata x, y):

public Polygon polygonFrom(Point[] corners) {
    // method body goes here
}

>**Nota:**  se vuoi passare un metodo in un metodo, usa un'espressione lambda o un riferimento al metodo.

## Numero arbitrario di argomenti

È possibile utilizzare un costrutto chiamato _varargs_ per passare un numero arbitrario di valori a un metodo. Usi varargs quando non sai quanti argomenti di un particolare tipo verranno passati al metodo. È una scorciatoia per creare manualmente un array (il metodo precedente avrebbe potuto utilizzare varags anziché un array).

Per utilizzare varargs, segui il tipo dell'ultimo parametro con i puntini di sospensione (tre punti, ...), quindi uno spazio e il nome del parametro. Il metodo può quindi essere chiamato con qualsiasi numero di quel parametro, incluso nessuno.

public Polygon polygonFrom(Point... corners) {
    int numberOfSides = corners.length;
    double squareOfSide1, lengthOfSide1;
    squareOfSide1 = (corners[1].x - corners[0].x)
                     * (corners[1].x - corners[0].x) 
                     + (corners[1].y - corners[0].y)
                     * (corners[1].y - corners[0].y);
    lengthOfSide1 = Math.sqrt(squareOfSide1);

    // more method body code follows that creates and returns a 
    // polygon connecting the Points
}

Puoi vedere che, all'interno del metodo, `corners` viene trattato come un array. Il metodo può essere chiamato con un array o con una sequenza di argomenti. Il codice nel corpo del metodo tratterà il parametro come una matrice in entrambi i casi.

Vedrai più comunemente varag con i metodi di stampa; ad esempio, questo `printf` metodo:

public PrintStream printf(String format, Object... args)

consente di stampare un numero arbitrario di oggetti. Può essere chiamato così:

System.out.printf("%s: %d, %s%n", name, idnum, address);

o così:

System.out.printf("%s: %d, %s, %s, %s%n", name, idnum, address, phone, email);

o con ancora un numero diverso di argomenti.

## Nomi dei parametri

Quando dichiari un parametro a un metodo oa un costruttore, fornisci un nome per quel parametro. Questo nome viene utilizzato all'interno del corpo del metodo per fare riferimento all'argomento passato.

Il nome di un parametro deve essere univoco nel suo ambito. Non può essere uguale al nome di un altro parametro per lo stesso metodo o costruttore e non può essere il nome di una variabile locale all'interno del metodo o del costruttore.

Un parametro può avere lo stesso nome di uno dei campi della classe. Se questo è il caso, si dice che il parametro _ombreggia_ il campo. L'ombreggiatura dei campi può rendere difficile la lettura del codice e viene convenzionalmente utilizzato solo all'interno di costruttori e metodi che impostano un campo particolare. Ad esempio, considera la seguente `Circle` classe e il suo `setOrigin` metodo:

public class Circle {
    private int x, y, radius;
    public void setOrigin(int x, int y) {
        ...
    }
}

La `Circle` classe ha tre campi: `x`, `y`, e `radius`. Il `setOrigin` metodo ha due parametri, ognuno dei quali ha lo stesso nome di uno dei campi. Ciascun parametro del metodo oscura il campo che ne condivide il nome. Quindi l'uso dei nomi semplici `x` o `y` all'interno del corpo del metodo fa riferimento al parametro, _non_ al campo. Per accedere al campo è necessario utilizzare un nome qualificato.

## Passaggio di argomenti di tipo di dati primitivi

Gli argomenti primitivi, come an `int`o a `double`, vengono passati ai metodi in _base al valore_ . Ciò significa che eventuali modifiche ai valori dei parametri esistono solo nell'ambito del metodo. Quando il metodo ritorna, i parametri sono spariti e tutte le modifiche ad essi vengono perse. Ecco un esempio:

public class PassPrimitiveByValue {

    public static void main(String[] args) {
           
        int x = 3;
           
        // invoke passMethod() with 
        // x as argument
        passMethod(x);
           
        // print x to see if its 
        // value has changed
        System.out.println("After invoking passMethod, x = " + x);
           
    }
        
    // change parameter in passMethod()
    public static void passMethod(int p) {
        p = 10;
    }
}

Quando si esegue questo programma, l'output è:

Dopo aver invocato passMethod, x = 3

## Passaggio di argomenti del tipo di dati di riferimento

Anche i parametri del tipo di dati di riferimento, come gli oggetti, vengono passati ai metodi in _base al valore_ . Ciò significa che quando il metodo ritorna, il riferimento passato fa ancora riferimento allo stesso oggetto di prima. _Tuttavia_ , i valori dei campi dell'oggetto _possono_ essere modificati nel metodo, se dispongono del livello di accesso appropriato.

Ad esempio, considera un metodo in una classe arbitraria che sposta `Circle` oggetti:

public void moveCircle(Circle circle, int deltaX, int deltaY) {
    // code to move origin of circle to x+deltaX, y+deltaY
    circle.setX(circle.getX() + deltaX);
    circle.setY(circle.getY() + deltaY);
        
    // code to assign a new reference to circle
    circle = new Circle(0, 0);
}

Sia invocato il metodo con questi argomenti:

moveCircle(myCircle, 23, 56)

All'interno del metodo, `circle` inizialmente si fa riferimento a `myCircle`. Il metodo modifica le coordinate x e y dell'oggetto a cui `circle`fa riferimento (ovvero `myCircle`) rispettivamente di 23 e 56. Queste modifiche persisteranno quando il metodo ritorna. Quindi `circle`viene assegnato un riferimento a un nuovo `Circle`oggetto con `x = y = 0`. Questa riassegnazione non ha però permanenza, perché il riferimento è stato passato per valore e non può cambiare. All'interno del metodo, l'oggetto a cui punta `circle`è cambiato, ma, quando il metodo ritorna, fa `myCircle` ancora riferimento allo stesso `Circle`oggetto di prima che il metodo fosse chiamato.