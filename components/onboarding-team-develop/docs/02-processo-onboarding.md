# Processo di Onboarding per Nuovi Team

## Ruoli e Responsabilità

Questo processo coinvolge vari attori con ruoli e responsabilità ben definite:

* **Team di Amministrazione del Sistema**: Responsabile della creazione degli account utente interni all'ambiente di sviluppo sicuro, configurazione dei permessi iniziali, e assegnazione dei profili di accesso necessari per l'operatività dei nuovi team.
* **Team di Sicurezza IT**: Gestisce l'integrazione dei nuovi membri nelle politiche di sicurezza esistenti e dell'accesso alla VPN, assicurando che tutte le connessioni e gli accessi siano conformi agli standard di sicurezza stabiliti.
* **Team di Supporto DevOps**: Fornisce supporto tecnico per l'integrazione degli strumenti di sviluppo e l'accesso agli ambienti di CI/CD, oltre a garantire che le configurazioni iniziali siano ottimali per il ciclo di vita del software.
* **Team di Formazione e Onboarding**: Ha il compito di fornire sessioni di formazione iniziale ai nuovi team, coprendo le best practices di sviluppo sicuro, l'uso corretto degli strumenti di sviluppo e le procedure operative standard.

## Procedura

Il referente del progetto richiede l'accesso per i propri utenti attraverso un sistema di ticketing, completando un modulo che specifica il livello di accesso necessario e le motivazioni. Ogni richiesta è esaminata e approvata da un responsabile della sicurezza. Tra i controlli è prevista la verifica che l'azienda di riferimento sia stata qualificata opportunamente presso l'Amministrazione.

Una volta approvata la richiesta, generalmente entro un paio di giorni lavorativi, a ciascun utente vengono comunicate le credenziali di connessione VPN e l'utente viene creato in LDAP tramite l'interfaccia web di CDP; infine vengono configurati i gruppi di appartenenza in KeyCloak. Il completamento della profilazione degli utenti nei gruppi GitLab e KeyCloak avviene automaticamente al primo login.

La rete raggiungibile dall'utente tramite la connessione VPN è parzializzata sulla base delle esigenze di raggiungere i vari sistemi descritte nel ticket di richiesta. Gli utenti vengono dunque ricondotti ad alcuni gruppi predefiniti di accesso, ed abilitati di conseguenza, per ridurre i rischi derivanti da movimento laterale non autorizzato sulla rete interna all'ambiente di sviluppo.

Durante l'onboarding i nuovi utenti ricevono formazione sulla sicurezza, sulla configurazione degli account e sull'uso degli strumenti; la procedura viene approfondita nell'apposito documento **AQDM-MIT-IntegrNuoviTeamPerAttivazione**. Viene seguita una checklist dettagliata che include tutti i passaggi necessari per integrare un nuovo membro nel team in modo sicuro ed efficiente.

Viene mantenuto un registro delle credenziali e degli accessi forniti all'utente, che viene integrato con i nuovi accessi forniti man mano che procede l'attività dell'utente nel sistema, per semplificare le procedure di offboarding.

## Timeline e Milestone

Il processo di onboarding è suddiviso in diverse fasi, ciascuna con milestone specifiche che assicurano una progressione ordinata e verificabile:

### Fase Preliminare (prima settimana):

Raccolta delle informazioni necessarie per la configurazione degli accessi. Creazione degli account utente nel sistema LDAP e assegnazione dei permessi di base. Setup degli ambienti di sviluppo e configurazione iniziale degli strumenti CI/CD.

### Fase di Formazione (seconda settimana):

Erogazione delle sessioni di formazione iniziale su sicurezza, processi di sviluppo, e gestione degli strumenti. Accesso alla documentazione di onboarding, contenente le linee guida (tra cui i presenti documenti), procedure e riferimenti a ulteriori risorse.

### Fase di Integrazione Operativa (terza \- quarta settimana):

Inizio delle attività operative con supervisione da parte del team di supporto DevOps. Verifica dell'integrazione con gli strumenti di monitoraggio e sicurezza per l'analisi statica del codice e JUnit per i test unitari. Prima esecuzione dei test automatizzati all'interno della pipeline CI/CD.

### Validazione (secondo mese):

Revisione e conferma della corretta configurazione degli accessi e delle autorizzazioni. Monitoraggio dei primi cicli di sviluppo e deploy per identificare eventuali problemi di conformità o di integrazione. Implementazione delle eventuali correzioni necessarie e consolidamento dell'ambiente operativo del team.

## Formazione sulla Sicurezza e sulle Best Practices

La sicurezza è un pilastro fondamentale del processo di onboarding. I nuovi team devono seguire un percorso formativo che copre tutti gli aspetti delle presenti Linee Guida, tra cui si evidenziano:

* **Politiche di Sicurezza dell'Accesso**: Uso di VPN, gestione delle credenziali, e autenticazione multifattoriale (MFA). Queste pratiche assicurano che l'accesso a GitLab e agli altri strumenti di sviluppo sia protetto.
* **Gestione delle Vulnerabilità**: Introduzione all'uso degli strumenti di sicurezza per l'analisi statica del codice, includendo il processo di gestione delle vulnerabilità e le politiche di remediation.
* **Best Practices di Codice**: Linee guida su come scrivere codice sicuro e aderente agli standard di qualità, con particolare attenzione all'uso dei test automatizzati e alla copertura del codice.

## Materiale e Risorse Disponibili

I nuovi team ricevono accesso a un repository centralizzato di documentazione che include manuali utente, documentazione tecnica, template e best practices. Tra i Manuali sono presenti guide dettagliate su come utilizzare gli strumenti di sviluppo, configurare l'ambiente di lavoro, e aderire alle politiche di sicurezza.

Nella documentazione tecnica sono inclusi casi d'uso, architettura applicativa, e architettura infrastrutturale, necessarie per comprendere il contesto tecnico dell'ambiente di sviluppo. Nei template e nelle best practices infine sono presenti modelli predefiniti per la scrittura della documentazione, dei casi di test, e del codice sorgente, per mantenere coerenza e qualità nel processo di sviluppo.

## Configurazione degli Accessi

La configurazione degli accessi è una delle prime attività durante l'onboarding e prevede innanzitutto la creazione dell'utenza: ogni nuovo membro riceve un account su LDAP, integrato con GitLab, gli strumenti di analisi di sicurezza, e gli altri strumenti necessari. Le credenziali iniziali sono distribuite tramite un canale sicuro, con un processo obbligatorio di cambio password al primo accesso.

Ogni utente viene associato a un profilo di accesso basato sul proprio ruolo con permessi specifici su GitLab e sui cluster Kubernetes tramite Keycloak. Dove possibile, l'accesso agli strumenti è centralizzato tramite Single Sign-On (SSO), riducendo la necessità di gestire più credenziali e semplificando il processo di accesso per gli utenti.
