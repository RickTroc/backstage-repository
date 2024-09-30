# Implementazione dei Test

## Best Practices per la Scrittura dei Test

I test devono essere chiari e semplici, descrivendo esattamente cosa viene testato e quale comportamento ci si aspetta. Evitare complessità inutili e assicurarsi che ogni test abbia un singolo scopo ben definito.

Ogni test deve essere indipendente dagli altri, in modo da evitare che un errore in un test influenzi l'esito di altri test. Utilizzare mocking e stubbing per isolare le dipendenze esterne.

I test devono essere ripetibili, garantendo lo stesso risultato ad ogni esecuzione. Evitare dipendenze dalla data corrente, da altri dati esterni variabili o da stati precedenti.

I test devono essere facili da leggere e mantenere. Utilizzare nomi di variabili e metodi descrittivi, e documentare chiaramente il comportamento testato.

## Naming Conventions

I nomi dei test devono essere descrittivi e indicare chiaramente quale funzionalità o comportamento viene verificato. La struttura raccomandata per i nomi dei test prevede un prefisso che identifica la classe o la funzionalità che si sta testando, poi un'indicazione della particolare azione o metodo che sta venendo invocato, ed infine una specificazione dello scenario o del risultato atteso.

Ad esempio, per unit test:

* testCalcoloTariffaTotale\_conInputValidi\_produceTotaleCorretto
* testAccettazionePratica\_conInputNonValidi\_produceException

Ad esempio, per test di integrazione:

* testAccettazionePratica\_creazione\_successo

Le classi di test devono essere denominate in modo da riflettere la classe o il modulo che testano; ad esempio, TariffServiceTest per testare la classe TariffService.

## Gestione delle Dipendenze

Utilizzare il paradigma Dependency Injection per registrare e passare le dipendenze necessarie ai test, evitando di creare oggetti all'interno dei test stessi. Questo migliora l'isolamento e facilita il mocking.

Utilizzare strumenti di mocking e stubbing per simulare il comportamento delle dipendenze esterne. Questo è particolarmente utile per isolare il codice testato e per testare scenari che potrebbero essere difficili da riprodurre con le dipendenze reali.

Assicurarsi che tutte le risorse utilizzate nei test (come connessioni a database o file) siano correttamente chiuse e ripulite dopo l'esecuzione dei test. Questo evita effetti collaterali e garantisce che i test siano ripetibili.

Per i test di integrazione è consigliato l'uso di container Docker per garantire ambienti di test isolati e consistenti. Questo approccio permette di eseguire test in ambienti che replicano accuratamente la produzione, riducendo il rischio di errori derivanti da differenze ambientali.

I test unitari e di integrazione dovrebbero utilizzare database in-memory, come H2, per garantire la velocità di esecuzione e ridurre la complessità nella gestione degli stati del database.
