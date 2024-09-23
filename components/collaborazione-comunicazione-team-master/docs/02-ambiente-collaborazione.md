# Ambiente di Collaborazione per i Team

## Strumenti di Gestione dei Progetti

L'ambiente di sviluppo sicuro dell'Amministrazione si avvale di strumenti consolidati per la gestione delle attività di progetto, con attenzione all'integrazione delle notifiche provenienti da vari sistemi automatici per garantire una comunicazione efficace e tempestiva tra i team.

Attualmente, per la gestione delle attività di sviluppo, viene utilizzato Jira, che consente di tracciare le issue, le user stories, e i task operativi per ciascun progetto. Attraverso Jira, è possibile assegnare attività specifiche ai membri del team e monitorarne l'avanzamento. Le attività relative alle fasi di sviluppo, testing, e deploy sono direttamente collegate ai workflow di lavoro, permettendo una gestione trasparente e centralizzata.

A supporto della collaborazione e della comunicazione quotidiana, l'Amministrazione utilizza Microsoft Teams, che può essere utile anche come piattaforma di riferimento per le riunioni virtuali e la messaggistica tra l'Amministrazione ed i membri del team. Teams è integrato con Jira, in modo da poter ricevere aggiornamenti e notifiche su task critici direttamente nei canali di comunicazione utilizzati dai team.

### Integrazione

Una caratteristica fondamentale dell'ambiente di sviluppo sicuro è la capacità di collegare tra loro le notifiche generate dai vari sistemi automatici per portare tempestivamente all'attenzione degli interessati il verificarsi di eventi rilevanti. Gli strumenti chiave in questo contesto includono GitLab e la Container DevSecOps Platform (CDP), che gestiscono i processi di build, deploy e sicurezza.

Ogni volta che una pipeline viene avviata, completata o fallisce, una notifica può essere inviata tramite il sistema di messaggistica di Teams. Anche il processo di deploy, gestito dalla CDP, genera notifiche automatiche al completamento delle varie fasi. In caso di successo, un messaggio può essere inviato tramite Teams o Jira per informare i responsabili del progetto. Se il deploy fallisce o incontra problemi di sincronizzazione tra componenti, come l'integrazione del database o il rilascio di container, una notifica viene inviata per allertare i team tecnici affinché intervengano.

Quando i test automatizzati (ad es. JUnit per i test di backend o Cerberus per i test end-to-end) falliscono, il sistema di gestione dei test invia notifiche ai membri del team. Queste notifiche includono il dettaglio del test fallito e, dove possibile, un link diretto al report di errore per facilitare una pronta diagnosi e risoluzione. Nel caso di Cerberus, le notifiche includono l’ID della sessione di test e un collegamento alla console di amministrazione per permettere una revisione più approfondita.

### Centralizzazione

Tutte le notifiche provenienti dai sistemi sopra descritti (GitLab, CDP, Jira, Teams, Cerberus) possono essere centralizzate in appositi canali di comunicazione tematici o di progetto all'interno di Microsoft Teams. Il referente per ciascun team può creare canali specifici per differenti attività (ad es. "Test", "Deploy", "Code Review") e configurare filtri e regole per gestire il flusso delle notifiche, garantendo che solo le informazioni rilevanti siano distribuite ai membri interessati. In questo modo, le notifiche critiche possono essere evidenziate in tempo reale, mentre quelle informative possono essere filtrate o raggruppate per una revisione successiva.

## Strumenti di Condivisione della Conoscenza

Nell'ambito dell'ambiente di sviluppo, la condivisione della conoscenza e la documentazione sono supportate da due principali sistemi: un repository dedicato collegato a Backstage per la gestione della documentazione tecnica del codice e un sistema dedicato per la raccolta della documentazione di progetto, trasversale ai singoli moduli software.

### Documentazione tecnica

La documentazione tecnica associata al codice sorgente sarà gestita tramite un repository dedicato, integrato con un'installazione di Backstage. Questo sistema consente di centralizzare e organizzare la documentazione tecnica, incluse le architetture applicative, i casi d'uso, i manuali utente e i manuali operativi, all'interno del ciclo di sviluppo. La struttura del repository tecnico segue le convenzioni stabilite nelle **AQDM-MIT-LineeGuidaRepository**, garantendo coerenza e facilità di accesso alle informazioni rilevanti per gli sviluppatori.

Backstage fornisce un'interfaccia unificata per la visualizzazione e la gestione di tutte le componenti documentali relative ai singoli moduli software. Tramite Backstage, gli sviluppatori possono accedere facilmente alla documentazione architetturale, agli schemi dei database, ai diagrammi di flusso del codice e ad altre risorse tecniche necessarie per comprendere e mantenere le diverse parti del sistema.

### Sistema Dedicato per la Documentazione di Progetto

Parallelamente alla gestione della documentazione tecnica, è stato implementato un sistema dedicato alla raccolta e alla gestione della documentazione di progetto, che riguarda aspetti trasversali ai singoli moduli software. Questo sistema ospiterà documenti come le specifiche funzionali, le pianificazioni di progetto, i report di avanzamento, le strategie di testing e la reportistica relativa alle attività di collaudo e verifica.

A differenza della documentazione strettamente tecnica, la documentazione di progetto serve un pubblico più ampio, che include non solo sviluppatori e architetti, ma anche stakeholder come Project Manager, referenti tecnici dell'Amministrazione e team di QA. Questo sistema garantisce che tutte le informazioni di progetto siano centralizzate e facilmente accessibili, promuovendo una visione complessiva e coerente del lavoro svolto.
