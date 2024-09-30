# Implementazione dell'Ambiente di Test

## Setup dell'Infrastruttura

L'implementazione dell'ambiente di test richiede la configurazione accurata dell'infrastruttura per supportare efficacemente l'automazione dei test e garantire che tutte le componenti del sistema siano testate in modo coerente e riproducibile. L'infrastruttura di test è progettata per essere flessibile, sicura e facilmente scalabile.

GitLab è utilizzato come sistema di gestione del codice sorgente e piattaforma CI/CD. Tutti i repository del codice sono ospitati su GitLab, che gestisce anche il controllo di versione, la code review, e l'integrazione con altri strumenti. Container DevSecOps Platform (CDP) è integrata con GitLab per orchestrare i processi di build, test e deploy. La CDP utilizza Kubernetes per gestire i container applicativi, assicurando che tutte le applicazioni siano costruite, testate e distribuite in modo uniforme.

Ogni progetto ha un ambiente di test dedicato, creato utilizzando container Docker orchestrati tramite Kubernetes. Questi ambienti sono isolati per garantire che i test non interferiscano tra loro e che ogni test possa essere eseguito in un ambiente controllato e prevedibile. I database per i test sono configurati utilizzando istanze containerizzate o in-memory, come H2 per test rapidi, o database containerizzati per test più complessi. Le configurazioni dei database sono sincronizzate con l'ambiente di produzione per garantire che i test riflettano le condizioni reali.

Tutti gli ambienti di test sono creati e distrutti automaticamente per ogni esecuzione di test. Questa automazione è gestita tramite script definiti nel repository del progetto e orchestrata dalla piattaforma CDP. Gli script includono la configurazione delle applicazioni, dei database e di altri servizi necessari per eseguire i test. Gli ambienti sono configurati per essere idempotenti, assicurando che possano essere riutilizzati o ripristinati allo stato iniziale senza interferenze da test precedenti. Gli script di setup e tear down garantiscono che le risorse siano utilizzate in modo efficiente e che i costi di infrastruttura siano minimizzati.

## Configurazione e Ambienti di Test

Ogni tool deve essere configurato per eseguire i test secondo criteri predefiniti, con parametri chiari per l'esecuzione e il reporting dei risultati.

Tutti gli ambienti di test sono containerizzati per garantire l'isolamento e la consistenza tra diverse esecuzioni di test. Questo approccio consente di replicare l'ambiente di produzione in modo preciso, riducendo le differenze tra ambiente di sviluppo, test e produzione. Gli ambienti containerizzati utilizzano immagini Docker specifiche per ciascun componente dell'applicazione. Queste immagini sono versionate e gestite tramite il registry Harbor integrato con la CDP, che garantisce che ogni esecuzione di test utilizzi la stessa versione dell'ambiente.

I dati di test sono gestiti utilizzando snapshot e script di migrazione che preparano il database in uno stato conosciuto prima di ogni esecuzione di test. Questo garantisce che i test siano riproducibili e che i risultati siano affidabili. Gli snapshot del database possono essere utilizzati per ripristinare rapidamente l'ambiente di test in caso di fallimenti, consentendo una diagnosi rapida e una correzione dei problemi senza necessità di ripetere l'intero ciclo di test.

### Gestione dei Database nei Test

Per contenere la dimensione della superficie della base dati da gestire nei test è importante individuare un perimetro di intervento che sarà oggetto degli script di predisposizione e ripristino all'avvio ed al completamento delle operazioni di test. All'interno dell'ambiente di sviluppo sicuro dell'Amministrazione, esistendo già il concetto di Sistema come raggruppamento per affinità funzionale di moduli, si raccomanda di considerare il Sistema in cui si trova il modulo in test come primo potenziale perimetro di copertura per le operazioni di preparazione e ripristino dei dati.

A seconda che i dati oggetto della preparazione siano all'interno del Sistema contenitore del modulo in test o meno, e a seconda che questi dati vengano "consumati" dall'esecuzione del test, si possono verificare alcune combinazioni. Nel caso in cui i dati siano ristretti al perimetro del Sistema contenitore, in autonomia si potranno predisporre gli script che preparano i dati consumabili e che verificano l'esistenza dei dati fissi. Se invece i dati necessari sono in un altro Sistema rispetto al Sistema contenitore, sarà opportuno fissare degli incontri con il relativo team responsabile così da poter pianificare la gestione dei dati fissi e le operazioni da eseguire o dei meccanismi di ripristino per la predisposizione dei dati consumabili.

### Test Unitari

Per JUnit, la configurazione include la definizione delle suite di test, l'integrazione con il sistema di build (Maven) e l'impostazione dei criteri di successo o fallimento. È essenziale che i test siano configurati per eseguire rapidamente e fornire feedback immediato agli sviluppatori, in modo da minimizzare i tempi di risoluzione dei bug.

All'interno dell'ambiente di sviluppo sicuro è già presente uno standard di impostazione dei test basata sull'abbinamento tra JUnit, Liquibase e H2. È prevista la predisposizione da parte degli sviluppatori, e l'attivazione durante l'esecuzione dei test, del properties profile denominato "test", contenente istruzioni per la gestione del database in-memory H2.

### Test End-to-End

Cerberus richiede una configurazione più dettagliata, poiché deve gestire test che coprono l'intero flusso applicativo. Questo include la definizione dei casi di test, la configurazione dei dati di test, e l'integrazione con i sistemi esterni necessari per simulare condizioni reali. Inoltre, Cerberus deve essere integrato con la pipeline CI/CD per eseguire i test automaticamente su ogni merge request e prima di ogni rilascio. L'Amministrazione raccoglie e mantiene la lista centralizzata dei casi di test per gli applicativi, separatamente dai singoli repository.

### Strumento di Analisi della Sicurezza del Codice

Sebbene lo strumento di analisi della sicurezza del codice sia utilizzato principalmente per l'analisi statica e dinamica, la sua configurazione deve permettere di correlare i risultati di sicurezza con quelli funzionali ottenuti da JUnit e Cerberus. Questo consente di avere una visione complessiva della qualità del codice, che include sia la sua funzionalità che la sua sicurezza.

### Analisi delle Prestazioni

Oltre ai test unitari e end-to-end, l'ambiente di test supporta anche test di integrazione e test di carico per valutare le prestazioni del sistema sotto stress. Gli strumenti come JMeter sono utilizzati per simulare il carico utente e testare le prestazioni del sistema. Gli ambienti di test sono configurati per includere strumenti di monitoraggio (Prometheus e Grafana) per raccogliere metriche dettagliate sulle prestazioni durante l'esecuzione dei test. Questi dati sono utilizzati per identificare colli di bottiglia e ottimizzare le prestazioni del sistema.
