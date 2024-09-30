# Definizione del Perimetro dei Test per i Casi d'Uso

## Criteri di Selezione dei Test

Le funzionalità critiche del sistema devono avere la massima priorità nei test. Questo include funzionalità che, se difettose, potrebbero causare gravi disservizi o compromettere la sicurezza del sistema, come ad esempio le funzionalità di autenticazione, parzializzazione dei coni di visibilità dei dati, misura dei KPI applicativi.

Le funzionalità utilizzate più frequentemente devono essere testate regolarmente per garantire che continuino a funzionare correttamente con ogni aggiornamento; anche le funzionalità che hanno storicamente presentato problemi o bug devono essere oggetto di test più approfonditi per assicurarsi che i problemi precedenti non si ripresentino. Ogni bug che viene risolto dovrebbe essere completato dall'aggiunta di uno o più casi di test che verifichino la persistenza del fix.

Le aree del sistema con molte interazioni complesse tra moduli o componenti devono essere testate per verificare che queste interazioni funzionino correttamente. In particolare, le funzionalità che riguardano la sicurezza o la conformità a standard regolamentari devono essere testate rigorosamente per assicurare il mantenimento della conformità prevista.

## Prioritizzazione dei Test

La prioritizzazione dei test aiuta a gestire efficacemente le risorse e il tempo, assicurando che i test più importanti siano eseguiti per primi. Assegnare la massima priorità ai test delle funzionalità critiche, assicurando che vengano eseguiti in ogni ciclo di test.

I test di regressione hanno una priorità immediatamente successiva, specialmente per le funzionalità che hanno subito modifiche recenti. Questo aiuta a garantire che le nuove modifiche non abbiano introdotto regressioni.

Poi vengono i test di integrazione per le aree del sistema dove i moduli o i componenti interagiscono. Questi test sono cruciali per garantire che le interazioni tra le diverse parti del sistema funzionino come previsto, ma possono prendere più tempo per via delle interazioni di set-up e tear-down. Potrebbero non essere eseguiti ad ogni singolo commit, ma solo nel momento di unione del codice nel branch di sviluppo, prima del relativo deploy.

I test di sicurezza possono invece essere spostati verso il fondo della catena, pur non dimenticando la loro importanza. Questi test aiutano a identificare e mitigare le vulnerabilità prima che possano essere sfruttate, ma richiedono che tutti i test di funzionamento precedente siano stati correttamente verificati.

## Definizione del Perimetro di Copertura

La copertura dei test deve essere completa e comprensiva di tutti i possibili scenari operativi che un utente potrebbe incontrare. La creazione di mappe di utilizzo che rappresentano i flussi di lavoro tipici degli utenti aiuta a identificare i percorsi critici e le aree del sistema che richiedono test approfonditi.

Ogni caso d'uso deve avere uno o più scenari di test associati che coprano condizioni normali, errori potenziali e casi limite. Gli scenari di test devono essere progettati per verificare sia il comportamento atteso che la gestione degli errori.

È importante testare diverse combinazioni di input per assicurare che il sistema gestisca correttamente tutti i possibili valori o combinazioni di dati. Questo include dati validi, invalidi, bordeline e potenzialmente dannosi.
