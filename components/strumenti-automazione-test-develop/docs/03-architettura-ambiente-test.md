# Architettura dell'Ambiente di Test Automatico

## Componenti dell'Architettura

L'architettura dell'ambiente di test automatico è stata progettata per garantire la coerenza, la sicurezza e la qualità del codice attraverso l'integrazione di strumenti specifici e processi automatizzati. L'ambiente include componenti chiave come il sistema di gestione del codice sorgente (GitLab), la piattaforma di Continuous Integration/Continuous Deployment (CI/CD) gestita dalla soluzione CDP, strumenti di analisi statica e dinamica della sicurezza, e piattaforme di testing automatizzato (JUnit per i test unitari e Cerberus per i test end-to-end).

### GitLab

Utilizzato come sistema di gestione del codice sorgente, GitLab ospita i repository di codice e gestisce il controllo di versione. È configurato per garantire l'accesso sicuro tramite VPN, e gli accessi e le autorizzazioni sono gestiti tramite LDAP, con profili configurati per sviluppatori, revisori, amministratori e altri ruoli specifici.

### CDP (Container DevSecOps Platform)

La piattaforma CDP gestisce le pipeline CI/CD per automatizzare il processo di build, test e deploy. Integrazioni strette con Kubernetes permettono una gestione efficiente del ciclo di vita delle applicazioni, inclusa la gestione delle configurazioni e dei segreti tramite Helm charts o manifest YAML.

### Analisi di sicurezza del codice

È presente uno strumento di analisi statica (SAST) e analisi della composizione del software (SCA) integrato nelle pipeline CI/CD per identificare vulnerabilità nel codice sorgente e nelle dipendenze di terze parti. Lo strumento è configurato per eseguire analisi su branch specifici del repository e produrre report di sicurezza che vengono monitorati tramite dashboard dedicate per avviare le azioni di remediation necessarie.

### JUnit

Utilizzato per eseguire test unitari di backend, JUnit è integrato nelle pipeline di GitLab per garantire che tutti i commit siano testati per il corretto funzionamento del codice. La copertura del codice è monitorata tramite appositi strumenti, con un obiettivo minimo di copertura fissato all'80%.

### Cerberus

Strumento per i test end-to-end automatizzati, utilizzato principalmente per le applicazioni web. Cerberus gestisce i test tramite una console web amministrativa e offre la possibilità di eseguire test su richiesta o come parte di una pipeline automatizzata. È configurato per integrarsi con il processo di deploy, assicurando che ogni rilascio sia testato accuratamente prima della promozione a un ambiente di produzione.

## Integrazione con l'Ambiente di Sviluppo

L'ambiente di test automatico è integrato strettamente con l'ambiente di sviluppo per garantire che le modifiche al codice siano verificate in modo continuo e che tutte le vulnerabilità e i bug siano identificati il prima possibile.

Lo strumento di analisi di sicurezza è integrato nelle pipeline CI/CD per eseguire analisi SAST e SCA. Ogni commit che supera la fase di test unitario viene sottoposto a un'analisi di sicurezza per garantire che il codice non introduca nuove vulnerabilità.

I test end-to-end sono integrati come una fase post-deploy nelle pipeline CI/CD. Cerberus può essere configurato per eseguire test completi su ambienti di staging o pre-produzione prima di una promozione in produzione. È possibile ottenere anche l'esecuzione di webhook e notifiche ai team al termine dell'esecuzione delle campagne di test, così da meglio inserire lo strumento nei flussi di lavoro.

## Integrazione con Container DevSecOps Platform (CDP)

L'ambiente di test automatico è integrato con CDP per facilitare il deployment sicuro e la gestione dei container. La CDP gestisce il ciclo di vita dei container, inclusi il loro build, test, deploy e promozione tra gli ambienti (sviluppo, staging, produzione).

Le pipeline di CI/CD sono configurate per eseguire automaticamente build e test a ogni commit. Le variabili di ambiente e i secret sono gestiti in modo sicuro all'interno della piattaforma Kubernetes.

La piattaforma offre strumenti per monitorare l'intero processo di deploy, inclusi report dettagliati che documentano ogni fase della pipeline CI/CD. Questi report sono utilizzati per tracciare e documentare le modifiche e le promozioni.

CDP integra strumenti di sicurezza per il monitoraggio continuo delle vulnerabilità del codice. Ogni nuova build deve passare attraverso controlli di qualità e sicurezza prima di essere promossa.

I risultati dei test sono monitorati tramite dashboard dedicate e notifiche automatiche sono inviate ai team di sviluppo in caso di fallimenti o problemi. Le notifiche includono dettagli sui test falliti, i motivi del fallimento e suggerimenti per la correzione. Report dettagliati sui test sono generati automaticamente e sono disponibili tramite la console di monitoraggio della CDP. Questi report sono utilizzati per l'analisi continua e l'ottimizzazione del processo di sviluppo.
