# Politiche di Test

## Tipi di Test (Unit, Integration, End-to-End)

Nel contesto di un ambiente di sviluppo sicuro, è essenziale definire chiaramente le tipologie di test da implementare per garantire la qualità e la sicurezza del codice. I tipi di test adottati sono i seguenti:

* Test Unitari (Unit Test): Questi test verificano il funzionamento di singole unità di codice, come funzioni o metodi. L'obiettivo è assicurarsi che ogni unità funzioni come previsto in isolamento. Sono fondamentali per identificare e correggere errori a livello di componente.
* Test di Integrazione (Integration Test): Verificano l'interazione tra diverse unità o componenti del sistema. Questi test sono cruciali per rilevare problemi nelle interfacce tra i moduli e garantire che le varie parti del sistema funzionino correttamente insieme.
* Test End-to-End (E2E): Simulano l'intero flusso dell'applicazione, dall'inizio alla fine. L'obiettivo è assicurarsi che tutte le parti del sistema lavorino insieme come previsto in un ambiente che replica il più possibile quello di produzione. Questi test sono particolarmente utili per applicazioni web e sistemi complessi, e nell'Ambiente di Sviluppo Sicuro il focus per i test end-to-end è sulle applicazioni web, utilizzando Cerberus.

## Copertura del Codice Richiesta

La copertura del codice è una metrica importante per valutare l'efficacia dei test. L'obiettivo minimo di copertura del codice è fissato all'80%, un valore che deve essere raggiunto e mantenuto attraverso test unitari e di integrazione. Questo obiettivo è impostato e monitorato tramite un apposito strumento che offre report dettagliati e permette di individuare le aree del codice non sufficientemente testate.

## Frequenza di Esecuzione dei Test

La frequenza di esecuzione dei test è determinata in base al tipo di test e all'evento che li innesca. I test unitari e statici sono eseguiti ad ogni push nel repository, permettendo di rilevare errori immediati e di mantenere una qualità costante del codice. I test di integrazione ed end-to-end sono invece eseguiti su ogni merge request, assicurando che le nuove modifiche non introducano regressioni o problemi di integrazione.

Regolarmente, ad esempio ogni notte, vengono eseguiti test completi di sicurezza; questo per mantenere l'integrità del codice senza aggiungere rallentamenti sul flusso di lavoro quotidiano.
