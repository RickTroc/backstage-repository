# Automazione e Integrazione

L'automazione e l'integrazione sono fondamentali per garantire che la documentazione rimanga aggiornata, coerente e facilmente accessibile in un approccio di tipo Documentatio as Code.

Sebbene il processo di gestione della documentazione possa includere validazioni manuali e procedure di deploy, l'obiettivo è automatizzare il più possibile attraverso pipeline di CI/CD, test automatici e deploy integrato con il **Developer Portal**.

Attualmente, alcuni passaggi richiedono ancora intervento manuale, ma ci sono strumenti e best practice per supportare il processo.

## Pipeline di CI/CD per la documentazione

Al momento non è stata implementata una pipeline di **CI/CD** (Continuous Integration/Continuous Deployment) specifica per la documentazione, ma questo rappresenta un obiettivo per migliorare l'automazione e ridurre gli errori manuali. Idealmente, una pipeline di CI/CD per la documentazione dovrebbe includere fasi di build, test, validazione e deploy automatizzato.

### Obiettivi futuri per la pipeline di CI/CD

1. **Build e generazione della documentazione**:

   - La documentazione può essere generata automaticamente utilizzando lo strumento **MkDocs** attualmente utilizzato da Backstage per generare i contenuti HTML. Quando viene eseguito un commit su GitLab, una pipeline CI/CD dovrebbe avviare il processo di build per generare la documentazione a partire dai file Markdown presenti nel repository.
   - La documentazione dovrebbe essere generata in formato PDF oltre che pubblicata in formato navigabile e ricercabile su Backstage.
2. **Validazione automatica**:

   - Una pipeline CI/CD dovrebbe includere fasi di validazione automatica, come il controllo della sintassi Markdown, la verifica dei link e il controllo della conformità agli standard di stile. Questi passaggi possono essere automatizzati usando strumenti come **markdownlint** o script personalizzati.
3. **Deploy automatico**:

   - La fase finale della pipeline dovrebbe essere il deploy automatico della documentazione su **Object Store** in formato PDF e su **Backstage** tramite l'integrazione con il modulo **techdocs-core**.

### Implementazione progressiva della pipeline

Fino a quando non sarà completamente implementata la pipeline CI/CD, è consigliabile:

- Effettuare semplici validazioni manuale, utilizzando il programma **MkDocs** in locale per visualizzare la documentazione generata e controllare la sua rispondenza alle aspettative.
- Documentare i passaggi manuali per la validazione e il deploy, in modo che possano essere standardizzati e facilmente automatizzati in futuro.

## 2. Test e validazione della documentazione

Poiché attualmente la validazione automatica della documentazione non è implementata, il test e la validazione devono essere eseguiti manualmente in locale. Questo processo si basa sull'utilizzo di **MkDocs**, un generatore di documentazione in Python, che permette di visualizzare e testare la documentazione prima di inviarla al repository.

### Processi per la validazione manuale

1. **Installazione di MkDocs**:

   - Prima di effettuare modifiche o testare la documentazione, assicurarsi di avere **MkDocs** ed il plugin **tech-docs** installato localmente. Se non è già installato, esegui il comando:

   ```bash
   pip install mkdocs mkdocs-techdocs-core
   ```

2. **Validazione locale della documentazione**:

   - Dopo aver apportato modifiche alla documentazione (ad esempio, file Markdown nel repository), è possibile generare e visualizzare la documentazione in locale. Usa il seguente comando nella directory che ospita il file `mkdocs.yml` per avviare il server di test locale:

   ```bash
   mkdocs serve
   ```

   Questo comando avvierà un server locale che renderizza la documentazione e la rende disponibile per la visualizzazione su un browser web. Il server si aggiorna automaticamente quando vengono salvate modifiche ai file Markdown.

3. **Verifica manuale della documentazione**:

   - Controlla manualmente che la struttura della documentazione, i link interni, le tabelle e i blocchi di codice siano corretti. Verifica che la documentazione generata segua le linee guida di formattazione e che le informazioni siano chiare e accurate.

4. **Debugging e correzioni**:

   - In caso di errori o formattazioni non corrette, è possibile apportare modifiche ai file Markdown e ricaricare la documentazione generata. **MkDocs** fornisce un feedback immediato sugli errori o problemi di sintassi.

### Strumenti aggiuntivi per il test:

- **markdownlint**: Uno strumento utile per eseguire controlli di sintassi e stile nei file Markdown, garantendo che il testo segua gli standard predefiniti.
  ```bash
  npm install -g markdownlint-cli
  markdownlint **/*.md
  ```

## 3. Deploy della documentazione sul Developer Portal

Il **deploy** della documentazione sul **Developer Portal** è un passaggio chiave per rendere le informazioni accessibili a tutto il team di sviluppo e agli altri stakeholder. Il deploy avviene grazie all'integrazione tra GitLab e il **Developer Portal**, basato su **Backstage** e il modulo **techdocs-core**.

### Processo di deploy tramite Backstage e TechDocs

1. **Configurazione del file `mkdocs.yml`**:

   - Ogni progetto che contiene documentazione deve includere un file di configurazione `mkdocs.yml`. Questo file definisce come la documentazione deve essere strutturata e come viene generata da **MkDocs**.

   **Esempio di `mkdocs.yml`**:

   ```yaml
   site_name: "Documentazione API Microservizio X"
   plugins: 
    - techdocs-core
   nav:
     - Home: index.md
     - API: api.md
     - Guida: guida_utente.md
   ```
2. **Configurazione del file `catalog-info.yaml`**:

   - Per integrare la documentazione con il **Developer Portal** basato su **Backstage**, è necessario configurare il file `catalog-info.yaml` nel repository GitLab. Questo file descrive il componente e la sua documentazione e permette a Backstage di importare e visualizzare i contenuti.

   **Esempio di `catalog-info.yaml`**:

   ```yaml
   apiVersion: backstage.io/v1alpha1
   kind: Component
   metadata:
     name: microservizio-X
     description: Documentazione del Microservizio X
     tags:
       - microservice
       - api
   annotations:
     backstage.io/techdocs-ref: dir:.
   spec:
     type: service
     owner: team-backend
     lifecycle: production
     system: sistema-X
     links:
       - url: 'https://gitlab.k8s01.sidt.local/project/microservizio-X'
         title: Repository GitLab
   ```
3. **Importazione della documentazione su Backstage**:

   - Una volta configurati `mkdocs.yml` e `catalog-info.yaml`, è possibile importare il repository su **Backstage**. Il file `catalog-info.yaml` consente a Backstage di riconoscere e indicizzare il progetto come componente documentato.
   - Nel portale di Backstage, seleziona l'opzione **"Register Existing Component"** e inserisci l'URL del repository GitLab contenente il file `catalog-info.yaml`.
   - Una volta importato, Backstage utilizzerà **techdocs-core** per generare automaticamente la documentazione e renderla disponibile nella sezione **TechDocs** del portale.
4. **Aggiornamento continuo**:

   - Dopo l'importazione iniziale, ogni volta che viene effettuata una modifica alla documentazione nel repository GitLab, Backstage sincronizza automaticamente la documentazione aggiornata. Ciò garantisce che le ultime versioni della documentazione siano sempre accessibili sul **Developer Portal**.

### Monitoraggio e controllo del deploy

- **Monitorare l'integrazione**: Dopo il deploy, verifica che la documentazione sia correttamente visualizzata su Backstage. Controlla che le pagine, i link e la struttura siano fedeli alle aspettative definite nel file `mkdocs.yml`.
- **Debug del processo di deploy**: In caso di errori o problemi nel deploy, controlla i log di **Backstage** e verifica che la configurazione di `mkdocs.yml` e `catalog-info.yaml` sia corretta.
