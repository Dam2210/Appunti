
La tecnologia Java è sia un linguaggio di programmazione che una piattaforma.

### Linguaggio di programmazione Java

Il linguaggio di programmazione Java è un linguaggio di alto livello che può essere caratterizzato da tutte le seguenti parole d'ordine:

- Semplice
- Orientato agli oggetti
- Distribuito
- Multithread
- Dinamico
- Architettura neutrale
- Portatile
- Alte prestazioni
- Robusto
- Sicuro

*Nota: queste parole d'ordine sono spiegate in 'The Java Language Environment' di James Gosling e Henry McGilton.

Nel linguaggio di programmazione Java, tutto il codice sorgente viene prima scritto in file di testo normale che terminano con *.javaestensione*. Questi file di origine vengono quindi compilati in *.classfile* dal *javac*compilatore. Un *.classfile* non contiene codive nativo del tuo processore; contiene invece *bytecode*, il linguaggio macchina virtuale di Java Virtual Machine (Java VM). Lo *javastrumento* di avvio esegue quindi l'applicazione con un'istanza di Java Virtual Machine.

![[Immagine2.png]]

Poichè Java VM è disponibile su molti sistemi operativi diversi, gli stessi *.classfile* possono essere eseguiti su Microsoft windows, il sistema operativo Solaris$^{TM}$ (Solaris OS), Linux, Mac OS. Alcune macchine virtuali, come Java SE HotSpot at a Glance, eseguono passaggi aggiuntivi in fase di esecuzione per aumentare le prestazioni dell'applicazione. Ciò include varie attività come la ricerca di colli di bottiglia nelle prestazioni e la ricompilazione (in codice nativo) di sezioni di codice utilizzate di frequente.

![[immagine3.png]]
*Attraverso la Java VM, la stessa applicazione è in grado di funzionare su più piattaforme.*

## La piattaforma Java

Una piattaforma è l'ambiente hardware o software in cui viene eseguito un programma. Abbiamo già menzionato alcune delle piattaforme più popolari come Microsoft Windows, Linux, Solaris OS e Mac OS. La maggior parte delle piattaforme può essere descritta come una combinazione del sistema operativo e dell'hardware sottostante. La piattaforma Java differisce dalla maggior parte delle altre piattaforme in quanto è una piattaforma solo software che funziona su altre piattaforme basate su hardware.

La piattaforma Java ha due componenti:
- La macchina virtuale Java
- L'API (Java Application Programming Interface)

La Java Virtual Machine è la base per la piattaforma Java ed è portata su varie piattaforme basate su hardware.
L'API è una vasta raccolta di componenti software già pronti che forniscono molte funzionalità utili. E' raggruppato in librerie di classi e interfaccie correlate; queste librerie sono conosciute come pacchetti. 

![[immagine4.png]]
*L'API e la Java VM isolano il programma dall'hardware sottostante.*

Essendo un ambiente indipendente dalla piattaforma, la piattaforma Java può essere leggermente più lenta del codice nativo. Tuttavia, i progressi nelle tecnologie dei compilatori e delle macchine virtuali stanno avvicinando le prestazioni a quelle del codice nativo senza compromettere la portabilità.

## Cosa può fare la tecnologia Java?

Il linguaggio di programmazione Java per uso generale e di alto livello è una potente piattaforma software. Ogni implementazione completa della piattaforma Java offre le seguenti funzionalità:
- **Strumenti di sviluppo:** gli strumenti di sviluppo forniscono tutto ciò di cui hai bisogno per compilare, eseguire e monitorare il debug e documentare le tue applicazioni. Come nuovo sviluppatore, gli strumenti principali che utilizzerai sono il *javac*compilatore, il *java*lanciatore e lo *javadoc*strumento di documentazione.
- **Application Programming Interface (API):** L'API fornisce le funzionalità principali del linguaggio di programmazione Java. Offre una vasta gamma di classi utili pronte per l'uso nelle proprie applicazioni. Si estende a tutto, dagli oggetti di base, al networking e alla sicurezza, alla generazione di XML e all'accesso al database e altro ancora.
- **Tecnologie di distribuzione:** il software JDK fornisce meccanismi standard come il software Java Web Start e il sofware Java Plug-In per la distribuzione delle applicazioni agli utenti finali.
- **Toolkit dell'interfaccia utente:** i toolkit JavaFX, Swing e Java 2D consentono di creare sofisticate interfaccie utente grafiche (GUI).
- **Librerie di integrazione:** le librerie di integrazione come Java IDL API, JDBC API, Java Naming and Directory Interface (JNDI) API, Java RMI e Java Remote Method Invocation consentono l'accesso al database e manipolazione di oggetti remoti.