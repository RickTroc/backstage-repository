# Versionamento e Gestione delle Modifiche

Un efficace sistema di versionamento e gestione delle modifiche è essenziale per garantire che la documentazione rimanga coerente e tracciabile, e che ogni modifica apportata sia accuratamente registrata e revisibile. Utilizzando strumenti di version control come **GitLab** e seguendo un modello di branching come **GitFlow**, è possibile mantenere la documentazione allineata con lo sviluppo del codice e gestire le versioni in modo strutturato.

## Utilizzo del version control per la documentazione

La documentazione tecnica segue lo stesso flusso di lavoro del codice sorgente, utilizzando **GitLab** come sistema di **version control**. Trattare la documentazione come codice (Documentation as Code) permette di applicare le stesse regole di versionamento, revisione e tracciamento utilizzate per il software, garantendo coerenza e controllo.

### Principi di version control per la documentazione:

- **Branch separati per ogni modifica**: Ogni modifica significativa alla documentazione viene effettuata su un **branch** dedicato. Questo permette di lavorare su nuove sezioni o aggiornamenti senza interferire con altre modifiche in corso. Ad esempio, per aggiornare la documentazione API di un microservizio, si può creare un branch `feature/update-api-docs`.

  **Esempio di comando Git**:

  ```bash
  git checkout -b feature/update-api-docs
  ```
- **Utilizzo di Merge Request (MR)**: Ogni modifica alla documentazione deve essere sottoposta a revisione tramite una **Merge Request**. Le Merge Request garantiscono che tutte le modifiche siano approvate da revisori prima di essere integrate nel branch principale, assicurando una revisione accurata e il controllo della qualità.
- **Integrazione con il codice**: La documentazione è strettamente legata al ciclo di vita del codice sorgente. Ogni modifica o aggiunta alla documentazione deve essere eseguita contemporaneamente ai cambiamenti del codice, in modo che siano allineati. Ad esempio, se viene introdotta una nuova funzionalità API, la relativa documentazione API deve essere aggiornata nello stesso branch.

### Benefici dell'utilizzo del version control per la documentazione:

- **Tracciabilità**: Ogni modifica è tracciata tramite commit, con la possibilità di visualizzare la cronologia delle modifiche e il loro autore.
- **Collaborazione**: I membri del team possono lavorare simultaneamente su diverse sezioni della documentazione senza conflitti, utilizzando branch dedicati.
- **Ripristino**: È possibile ripristinare versioni precedenti della documentazione in caso di errori o problemi, grazie al sistema di versionamento Git.

## Gestione delle versioni della documentazione

Così come il software, anche la documentazione deve seguire un processo di **versioning** strutturato, che permetta di mantenere diverse versioni allineate con i rilasci del software. Ogni nuova versione del prodotto software deve essere accompagnata da una versione della documentazione, garantendo che le informazioni fornite siano sempre accurate e aggiornate rispetto alla versione del codice rilasciata.

### Linee guida per la gestione delle versioni:

- **Branch principali**:

  - **master**: Contiene la versione stabile della documentazione, allineata con la versione di produzione del software.
  - **develop**: Contiene la documentazione più aggiornata in preparazione per il prossimo rilascio, allineata con le modifiche del codice non ancora rilasciato in produzione.
- **Tag e release**:

  - Ogni rilascio di una nuova versione del software deve essere accompagnato da un **tag** nel repository della documentazione. I tag permettono di marcare un commit specifico come rappresentante di una versione del prodotto. Ad esempio, il tag `v1.2.0` indicherà che la documentazione è allineata con la versione `1.2.0` del software.

  **Esempio di comando per il tagging**:

  ```bash
  git tag -a v1.2.0 -m "Documentazione per la release v1.2.0"
  git push origin v1.2.0
  ```
- **Gestione delle versioni tramite GitFlow**:

  - Il modello **GitFlow** aiuta a strutturare il lavoro di sviluppo e la gestione delle versioni della documentazione. Ogni feature o modifica viene sviluppata su un branch `feature/`, mentre per la preparazione delle versioni di rilascio si utilizza un branch `release/`. Al termine del ciclo di sviluppo, la documentazione aggiornata viene fusa nei branch `develop` e `master` e viene creato un tag per marcare il rilascio.

### Esempio di flusso GitFlow per la documentazione:

1. **Feature branch**: Creare un branch per sviluppare una nuova sezione della documentazione o per aggiornarla.

   ```bash
   git checkout -b feature/documentazione-nuova-api
   ```
2. **Merge nel branch develop**: Dopo la revisione, il branch `feature/` viene fuso nel branch `develop`, in attesa del rilascio della nuova versione.

   ```bash
   git checkout develop
   git merge feature/documentazione-nuova-api
   ```
3. **Release branch**: Prima del rilascio, creare un branch `release/` per finalizzare la documentazione.

   ```bash
   git checkout -b release/1.2.0
   ```
4. **Merge in master e tag**: Dopo il testing e la revisione finale, il branch `release/` viene fuso in `master`, e viene creato un tag per la versione rilasciata.

   ```bash
   git checkout master
   git merge release/1.2.0
   git tag -a v1.2.0 -m "Release v1.2.0"
   git push origin master --tags
   ```

## Tracciamento delle modifiche e changelog

Ogni modifica alla documentazione deve essere tracciata e documentata in modo da garantire trasparenza e comunicare chiaramente agli utenti quali aggiornamenti sono stati effettuati. Il **changelog** è uno strumento fondamentale per comunicare le modifiche alla documentazione e per mantenere uno storico chiaro e consultabile.

### Creazione e gestione del changelog:

- **Changelog per ogni versione**: Ogni rilascio di una nuova versione della documentazione deve includere un aggiornamento del changelog. Questo documento elenca tutte le modifiche rilevanti apportate alla documentazione, come aggiunte di nuove sezioni, modifiche ai contenuti esistenti o correzioni di errori.

  **Struttura tipica di un changelog**:

  ```markdown
  # Changelog

  ## [v1.2.0] - 2024-09-15
  ### Aggiunto
  - Aggiunta la documentazione per il nuovo endpoint API `POST /prenotazioni`
  - Aggiunte le linee guida per la gestione dei conflitti di prenotazione

  ### Modificato
  - Aggiornata la sezione di autenticazione con i nuovi parametri OAuth2
  - Migliorate le descrizioni dei parametri dell'API `/users`

  ### Risolto
  - Corretto un errore nella descrizione della risposta dell'API `/resources`
  ```
- **Commit descrittivi**: Ogni commit che introduce modifiche alla documentazione deve includere un messaggio descrittivo che spieghi chiaramente cosa è stato cambiato. Questo permette di mantenere uno storico dettagliato delle modifiche e facilita la generazione del changelog.

  **Esempio di commit**:

  ```bash
  git commit -m "Aggiunta la documentazione per il nuovo endpoint POST /prenotazioni"
  ```
- **Integrazione del changelog nel processo di rilascio**: Al momento del rilascio di una nuova versione del software, il changelog aggiornato deve essere incluso nel processo di **release** e pubblicato insieme alla nuova versione della documentazione. Ciò assicura che tutti gli utenti possano facilmente consultare le modifiche introdotte nella versione corrente.

### Strumenti per il tracciamento delle modifiche:

- **Git**: Lo strumento principale per il tracciamento delle modifiche alla documentazione, che consente di visualizzare la cronologia delle modifiche, i commit e le differenze tra le versioni.

  **Esempio di visualizzazione della cronologia**:

  ```bash
  git log --oneline
  ```
- **GitLab Changelog**: GitLab può generare changelog automaticamente dai tag e dai commit, facilitando la gestione e la comunicazione delle modifiche apportate.
