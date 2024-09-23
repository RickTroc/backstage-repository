# Regole e procedure di gestione del repository

## Struttura del repository

La struttura del repository del codice è fondamentale per mantenere un'organizzazione chiara e coesa del progetto.

All'interno della base di codice gestito dall'Amministrazione si identificano dei domini di competenza, denominati "Sistemi", e rappresentati all'interno del repository GitLab come un gruppo che contiene vari moduli o componenti logici, come microservizi, frontend SPA (Single Page Applications), e backend API.

La suddivisione in Sistemi è utile per migliorare la manutenibilità e viene individuata dagli architetti e dagli analisti funzionali, ed oltre alle applicazioni nel repository può includere modalità specifiche di gestione, un linguaggio/gergo di dominio, documentazione, e quant'altro necessario a caratterizzarli.

I repository di un Sistema possono includere anche alcune librerie di dipendenza base comuni alle componenti del Sistema, oppure comuni alle applicazioni di più sistemi; in quest'ultimo caso vengono comunque ricondotte per affinità nell'ambito di un Sistema.

La struttura delle cartelle all'interno di ogni repository è determinata dalla tecnologia utilizzata. Per esempio, un progetto Java potrebbe avere cartelle distinte per "src", "test", e "resources". La documentazione associata al codice, come i manuali utente e i documenti di architettura, è da conservare sia nel repository git che in repository dedicati a livello di sistema.

## Nomenclatura

I gruppi all'interno dello strumento GitLab seguono due modalità di denominazione; la prima è relativa ai gruppi per team trasversali, come ad esempio i nomi dei singoli fornitori, mentre la seconda modalità è per ciascun Sistema. I gruppi che rappresentano i Sistemi sono denominati con un nome breve, per esteso, che identifica il Sistema (ad es. "Patenti").

Ogni repository segue una convenzione con un prefisso di nomenclatura standard che include il nome del sistema (codice breve di quattro caratteri) e il tipo di applicazione. Ad esempio, per una SPA all'interno del sistema "Patenti", il nome del repository potrebbe essere "PATN-SPA-RichiestaPatenti". La coerenza nella nomenclatura è cruciale per facilitare la manutenzione del codice e la collaborazione tra team. La mappa delle abbreviazioni per le tipologie applicative ad oggi è la seguente:

* Single Page Application (frontend React) → SPA
* Microservizio (backend Java) → MS
* Backend-for-frontend (backend Java) → BFF

La nomenclatura coerente e standardizzata per file, cartelle e branch è essenziale per la manutenibilità e la chiarezza del codice. I nomi dei file e delle cartelle devono essere descrittivi e seguire una convenzione predeterminata che include il tipo di componente e la funzionalità. I nomi dei branch devono seguire una convenzione specifica, ad esempio, "feature/nome-feature", "release/nome-release", e "hotfix/nome-hotfix"; la gestione del branching deve essere conforme al modello Gitflow, descritto nel paragrafo seguente.

Tutti i membri del team devono essere informati delle convenzioni di nomenclatura attraverso documentazione chiara e accessibile, come questo documento o sue specificazioni od integrazioni.

## Strategie di Branching

La gestione efficace dei branch è cruciale per un flusso di lavoro ordinato e collaborativo; un buon approccio aiuta a mantenere ordine e chiarezza nel processo di sviluppo.

I tag sono utilizzati per segnare versioni specifiche del codice, facilitando il tracking delle release e delle milestone importanti.

I conflitti di merge devono essere risolti con il coinvolgimento dei technical leader quando necessario. Le politiche per la risoluzione dei conflitti includono l'uso di strumenti di merge e la revisione del codice.

I branch obsoleti o non più necessari devono essere regolarmente rimossi per mantenere il repository pulito e gestibile.

### Gitflow

Il modello Gitflow è adottato come strategia principale di branching per garantire un processo di sviluppo strutturato e coerente. Gitflow distingue tra i seguenti tipi di branch:

* Master: contiene la versione stabile e pronta per la produzione del codice. Ogni commit sul branch master rappresenta una nuova release.
* Develop: riflette lo stato corrente del prossimo rilascio. Tutte le nuove funzionalità e le correzioni di bug sono integrate qui prima di essere eventualmente rilasciate.
* Feature: creati dal branch develop per lo sviluppo di nuove funzionalità. Una volta completata la funzionalità, questi branch sono fusi nel develop e rimossi.
* Release: derivano dal develop quando si è pronti per iniziare la fase di preparazione di una nuova release. Dopo aver corretto eventuali bug e finalizzato la release, il branch è unito sia al develop che al master. Il branch passa dunque in uno stato protected
* Hotfix: utilizzati per le correzioni urgenti dei bug sulla versione di produzione. I branch hotfix derivano dal master e, una volta risolto il problema, vengono uniti al master e al develop.

Questa strategia permette di mantenere un flusso di lavoro chiaro e ben definito, facilitando la gestione delle varie fasi del ciclo di vita del software.

### Gestione dei Feature Branch

I feature branch sono utilizzati per lo sviluppo di nuove funzionalità. Ogni feature branch deve essere creato dal develop e, una volta completata la funzionalità, deve essere unito di nuovo al develop. È importante utilizzare un nome descrittivo per il branch che rappresenti chiaramente la funzionalità in sviluppo; ad esempio, feature/nome-funzionalità. I feature branch dovrebbero avere una durata limitata, al fine di ridurre la complessità e il rischio di conflitti di merge.

È opportuno integrare regolarmente i cambiamenti dal develop al feature branch (rebase) per mantenere il codice aggiornato e ridurre i conflitti. È importante evitare il merge di develop nel feature branch, soprattutto quando sono aperti più feature branch in parallelo, e preferire il rebase; il rischio è di andare a storicizzare in un merge commit una versione del sorgente di develop che è rimasta indietro rispetto ad eventuali commit di novità negli altri feature branch, andando così a complicare il merge automatico dell'ultimo feature branch che viene portato in develop.

Ogni feature branch deve essere sottoposto a una revisione del codice prima della fusione nel develop per garantire la qualità del codice e il rispetto degli standard.

### Gestione delle Release

I release branch sono creati quando si è pronti per iniziare il processo di rilascio di una nuova versione. Questi branch permettono di preparare il codice per la produzione, risolvendo eventuali bug e completando le attività di test.

Il branch di release viene creato dal develop quando tutte le funzionalità previste per la nuova versione sono state integrate. Durante la fase di stabilizzazione, si effettuano solo test e correzioni di bug e altre modifiche necessarie per preparare la release.

Una volta che il branch di release è pronto, viene fuso sia nel master che nel develop. Questa fusione garantisce che le correzioni effettuate durante la fase di stabilizzazione siano incluse nel ramo principale di sviluppo.

### Hotfix e Bugfix

Gli hotfix branch sono utilizzati per risolvere bug critici trovati nella versione di produzione. La gestione di questi branch segue delle pratiche specifiche: infatti gli hotfix branch sono creati direttamente dal master per affrontare problemi urgenti che devono essere risolti immediatamente.

Dopo aver implementato la correzione, il branch hotfix è sottoposto a test approfonditi per garantire che il problema sia risolto senza introdurre nuovi bug. Una volta verificata la correzione, il branch hotfix viene fuso nel master e nel develop, assicurando che la correzione sia disponibile nella versione di produzione e nel flusso di sviluppo continuo.

## Processo di Code Review

Il processo di code review è essenziale per mantenere la qualità del codice e garantire che le modifiche siano allineate con gli standard del progetto. Ogni modifica al codice deve passare attraverso una review da parte di uno o più membri del team. Questo aiuta a identificare errori, migliorare la qualità del codice, e diffondere la conoscenza tra i team.

Le code review devono essere documentate e tracciabili tramite GitLab; i revisori devono fornire feedback chiaro e costruttivo. GitLab offre strumenti integrati per la code review, come ad esempio le merge request, che facilitano il processo di revisione e approvazione delle modifiche al codice. La configurazione di dashboard e reportistica aiuta a monitorare lo stato delle review e a garantire che tutte le modifiche siano state adeguatamente valutate.

L'integrazione di strumenti di analisi statica di qualità e di sicurezza nelle pipeline CI/CD va ad integrare il processo di review, identificando automaticamente vulnerabilità e problemi di qualità ed aggiungendo questi dati come commento nei flussi di discussione.
