# Principi Fondamentali

## Definizione di Documentation as Code

**Documentation as Code (DaC)** è un approccio alla creazione e gestione della documentazione che applica le pratiche tipiche dello sviluppo software alla documentazione stessa. Questo paradigma considera la documentazione un elemento strettamente integrato con il codice sorgente, trattandola come parte essenziale del ciclo di sviluppo.

Nell'approccio DaC, la documentazione viene gestita utilizzando gli stessi strumenti e processi del codice, come il version control, l'automazione attraverso pipeline di CI/CD e la revisione collaborativa tramite pull request. Questo garantisce che la documentazione sia costantemente aggiornata e mantenuta coerente con lo stato attuale del progetto, riducendo il rischio di discrepanze tra ciò che è documentato e ciò che è effettivamente implementato.

Le caratteristiche principali di **Documentation as Code** includono:

- **Versionamento**: La documentazione è soggetta a version control (tramite Git), permettendo di tracciare modifiche, eseguire rollback e mantenere uno storico delle revisioni, proprio come accade con il codice.
- **Revisione Collaborativa**: Le modifiche alla documentazione vengono gestite tramite pull request, consentendo al team di rivedere, discutere e approvare i cambiamenti prima che vengano integrati.
- **Automazione**: I processi di generazione, verifica e distribuzione della documentazione possono essere automatizzati tramite pipeline CI/CD, assicurando che ogni modifica venga validata e pubblicata senza intervento manuale.
- **Integrazione Continua**: La documentazione è integrata nel flusso di sviluppo, il che significa che viene aggiornata insieme al codice, evitando che diventi obsoleta o incoerente.

In sintesi, **Documentation as Code** promuove una documentazione sempre aggiornata, collaborativa e automatizzata, integrando completamente la gestione della documentazione nel ciclo di sviluppo agile.

## Vantaggi di Documentation as Code

Adottare l'approccio **Documentation as Code** comporta una serie di vantaggi significativi rispetto ai metodi tradizionali di gestione della documentazione. Questi benefici emergono dall'integrazione della documentazione nel ciclo di vita del software, rendendola parte integrante del flusso di lavoro di sviluppo e migliorandone la qualità e la mantenibilità.

I principali vantaggi includono:

- **Allineamento costante con il codice**: La documentazione viene aggiornata insieme al codice sorgente. Questo riduce il rischio di discrepanze tra il codice implementato e quanto descritto nei documenti, garantendo che la documentazione rifletta sempre lo stato attuale del progetto.
- **Versionamento e tracciabilità**: Con l'utilizzo di sistemi di version control (come Git), ogni modifica alla documentazione è tracciabile. Questo permette di conoscere la storia delle modifiche, di identificare chi ha modificato cosa e di ripristinare versioni precedenti se necessario.
- **Collaborazione migliorata**: La documentazione diventa un'attività collaborativa grazie all'uso delle pull request, che consentono ai membri del team di rivedere, discutere e approvare modifiche prima che queste vengano integrate. Questo assicura che più persone partecipino attivamente al miglioramento continuo della documentazione.
- **Automazione del processo di documentazione**: Le pipeline di CI/CD possono essere configurate per automatizzare processi come la generazione della documentazione, i controlli di qualità e il deploy su piattaforme di hosting. Questo elimina la necessità di operazioni manuali, riducendo il rischio di errori e risparmiando tempo prezioso.
- **Miglioramento della qualità**: L'integrazione dei test automatici anche per la documentazione, come la validazione dei link, l'analisi della leggibilità o la verifica del formato, contribuisce a migliorare la qualità complessiva della documentazione. Questo assicura che sia sempre accurata, accessibile e ben strutturata.
- **Facilità di manutenzione**: Poiché la documentazione è gestita nello stesso repository del codice, i processi di aggiornamento e manutenzione vengono eseguiti con la stessa efficienza e organizzazione del ciclo di sviluppo del software. Questo riduce l'onere di dover gestire la documentazione separatamente dal codice.
- **Standardizzazione**: L'approccio DaC permette di applicare regole e formati standardizzati per tutta la documentazione del progetto. Questo rende i documenti più coerenti, facili da leggere e mantenere, migliorando l’esperienza degli utenti e degli sviluppatori.
- **Trasparenza e accountability**: Grazie alla tracciabilità e alla revisione collaborativa, è sempre chiaro chi è responsabile di una modifica alla documentazione, aumentando la trasparenza e la responsabilità all'interno del team.

In conclusione, l'adozione di **Documentation as Code** porta numerosi benefici in termini di coerenza, efficienza, qualità e collaborazione, rendendo la documentazione un asset vivo e gestibile nel tempo, esattamente come il codice sorgente.

## Best Practice per la gestione continua della documentazione

L'adozione di **Documentation as Code** richiede una serie di buone pratiche che consentano di mantenere la documentazione sempre aggiornata e in linea con l'evoluzione del progetto. La **documentazione continua** non è solo un'attività una tantum, ma un processo iterativo che si svolge parallelamente allo sviluppo del software. Di seguito sono elencate alcune delle migliori pratiche per garantire che la documentazione rimanga accurata, utile e di qualità nel tempo.

### Documentare in parallelo allo sviluppo

La documentazione deve essere aggiornata contestualmente alle modifiche del codice. Ogni nuova funzionalità, modifica o correzione di bug che comporta cambiamenti nel comportamento del software, nelle API o nell'architettura deve essere accompagnata dalla relativa documentazione. Questo approccio assicura che la documentazione non diventi obsoleta e che rispecchi fedelmente lo stato attuale del progetto e garantisce che gli utenti e gli sviluppatori abbiano sempre accesso a informazioni corrette e aggiornate.

**Esempio**: Se uno sviluppatore introduce una nuova API per recuperare i dati degli utenti, oltre al codice dovrà creare o aggiornare la documentazione API. Questo può includere la descrizione dell'endpoint, i parametri di input, il formato della risposta, eventuali codici di errore e un esempio di richiesta e risposta. La documentazione deve essere inclusa nello stesso pull request che contiene il codice della nuova API, in modo che possa essere revisionata insieme al codice.

Ecco come potrebbe essere gestita l'aggiunta della documentazione:

- Aggiungere un file `doc/api/users.md` nel repository della documentazione con la descrizione completa dell'API.
- Nel commit associato, includere un messaggio come:
  `"Aggiunta documentazione per l'API /users [refs #1234]"`, dove `#1234` si riferisce al numero del ticket che ha originato la nuova funzionalità.

In questo modo, ogni modifica rilevante al codice ha una corrispondente modifica alla documentazione, mantenendo allineati codice e documentazione e garantendo che siano sempre aggiornati contemporaneamente.

### Utilizzare il version control per la documentazione

È fondamentale versionare la documentazione nello stesso repository del codice sorgente. Questo consente di mantenere una cronologia completa delle modifiche, associandole a commit specifici. In questo modo, è possibile visualizzare l'evoluzione della documentazione in relazione a specifici cambiamenti nel software.

La documentazione deve essere, dunque, gestita tramite il sistema di **version control Git**  e seguire il flusso di lavoro **GitFlow** adottato nella gestione dei repository. Questo approccio organizza il lavoro in branch specifici per ogni fase dello sviluppo (feature, release, hotfix), garantendo che la documentazione segua esattamente lo stesso ciclo del codice sorgente. Versionare la documentazione assicura tracciabilità, storico delle modifiche e la possibilità di eseguire rollback in caso di necessità, garantendo che ogni modifica sia collegata a una specifica funzionalità o correzione del software.

**Esempio**: Riprendendo l'esempio della nuova API `/users` per il recupero dei dati degli utenti, la gestione della documentazione seguendo GitFlow sarà organizzata come segue:

1. **Creazione di un branch feature**: Lo sviluppatore, seguendo il modello GitFlow, crea un branch `feature/add-user-api` a partire dal branch `develop`, che è il branch di sviluppo principale. In questo branch lavorerà sia sulla nuova funzionalità che sulla documentazione.

```
  git checkout develop
  git checkout -b feature/add-user-api
```

2. **Modifiche al codice e alla documentazione**:

* Nel codice, viene implementata la nuova API `/users`.
* Contestualmente, nel branch `feature/add-user-api`, viene creato o aggiornato il file `api/users.md` per includere tutte le informazioni rilevanti: descrizione dell'endpoint, parametri di input, formato della risposta e un esempio di richiesta e risposta.

3. **Commit delle modifiche**: Una volta completato lo sviluppo della funzionalità e l'aggiornamento della documentazione, lo sviluppatore esegue un commit che include sia le modifiche al codice sia la documentazione aggiornata.

* Effettuare il commit delle modifiche:

```
  git add .
  git commit -m "Implementazione dell'API /users e aggiunta della documentazione API [refs #1234]"
```

4. **Apertura di una pull request verso develop**: Quando la funzionalità è completa e testata, lo sviluppatore apre una pull request dal branch feature/add-user-api al branch develop.

* Nella pull request verranno revisionati sia il codice sia la documentazione, assicurandosi che nessuna nuova funzionalità venga integrata senza la relativa documentazione.

5. **Merge nel branch develop**: Dopo che la pull request viene approvata, il branch feature/add-user-api viene fuso nel branch develop. La documentazione e il codice vengono quindi sincronizzati nel branch di sviluppo principale, preparandosi per il prossimo ciclo di rilascio.

```
  git checkout develop
  git merge feature/add-user-api
```

6. **Preparazione per il rilascio**: Quando è pronta una nuova release, viene creato un branch release, ad esempio release/v1.2.0, a partire da develop. Durante questa fase, eventuali aggiornamenti finali alla documentazione (ad es. dettagli della release) vengono apportati nel branch release.
7. **Merge in master e hotfix**: Una volta che il branch release è stabile, viene fuso nel branch master per il rilascio in produzione. A questo punto, la documentazione e il codice vengono distribuiti insieme. Nel caso in cui si debbano applicare correzioni rapide (hotfix), vengono creati branch hotfix a partire da master e, come per le feature, eventuali aggiornamenti alla documentazione relativi a correzioni critiche vengono inclusi nei commit di hotfix.
8. **Storico e tracciabilità**: Tutte le modifiche alla documentazione sono ora tracciate all'interno del repository Git. Utilizzando comandi come git log o git blame, è possibile visualizzare la cronologia delle modifiche alla documentazione e associarle ai cambiamenti del codice. Questo approccio garantisce che ogni cambiamento documentato sia legato a una specifica modifica del software, mantenendo una corrispondenza continua tra codice e documentazione.

```
  git log -- doc/api/users.md
```

### Coinvolgere tutto il team

La documentazione non è solo responsabilità di un gruppo dedicato; tutto il team dovrebbe essere coinvolto. Gli analisti, gli sviluppatori, i product owner, i QA, gli esperti di sicurezza e, più in generale, tutto il team DevSecOps devono contribuire alla creazione e al mantenimento della documentazione.

Un processo di revisione collaborativa, come l'utilizzo di pull request per la documentazione, facilita il coinvolgimento di tutti i membri del team.

Nel paradigma **Documentation as Code**, la documentazione non è responsabilità esclusiva di un singolo individuo o team dedicato. Invece, deve essere vista come un'attività collaborativa che coinvolge tutto il team di sviluppo, comprese le figure di analisti, architetti, sviluppatori, QA, DevOps e product owner. Il coinvolgimento di tutto il team garantisce che la documentazione sia accurata, aggiornata e comprensibile, riflettendo al meglio il lavoro svolto nel progetto.

In un contesto Agile **Scrum-like**, quale quello adottato dall'Amministrazione, l'integrazione della documentazione nel processo di sviluppo può essere organizzata in modo procedurale durante i vari eventi Scrum, per garantire una collaborazione continua e strutturata.

**Attività procedurali in un ciclo per garantire il coinvolgimento del team nella redazione della documentazione:**

1. **Definizione della documentazione nelle User Story**
   Durante la **Sprint Planning**, ogni User Story dovrebbe includere esplicitamente i requisiti per la documentazione. Gli Acceptance Criteria devono considerare la creazione o l'aggiornamento della documentazione come parte integrante della Story. Questo garantisce che la documentazione non venga trascurata e che faccia parte della Definition of Done.

   **Esempio**: Se viene pianificata la User Story "Come utente, voglio recuperare una lista di utenti tramite l'API `/users`", uno degli Acceptance Criteria potrebbe essere:`"La documentazione dell'API `/users ` deve essere creata/aggiornata con descrizione, parametri, risposta e codici di errore."`
2. **Aggiornamento continuo della documentazione durante lo sviluppo**
   Durante lo **Sprint**, lo sviluppatore o il membro del team responsabile della User Story non solo implementerà il codice, ma aggiornerà anche la documentazione in parallelo. Questo avviene nel branch Git assegnato alla Story, dove sia il codice che la documentazione vengono trattati insieme.

   **Esempio**: Se uno sviluppatore sta implementando la nuova API `/users`, lavorerà nel branch `feature/add-user-api`, in cui aggiornerà sia il codice che la documentazione corrispondente (es. `doc/api/users.md`). Quando crea il commit o apre una pull request, includerà sia le modifiche al codice che quelle alla documentazione, rispettando il processo di revisione definito.
3. **Daily Meeting e aggiornamenti sulla documentazione**
   Durante il **Daily Meeting**, ogni membro del team può riferire non solo sullo stato del codice, ma anche sulla documentazione correlata. Questo aiuta a mantenere la trasparenza e ad evidenziare eventuali difficoltà o ritardi nella redazione della documentazione. Se necessario, possono essere richiesti supporto o revisione da altri membri del team.

   **Esempio**: Uno sviluppatore potrebbe menzionare durante il Daily Scrum:`"Sto lavorando sull'implementazione dell'API `/users ` e ho quasi completato la documentazione corrispondente. Oggi finirò il commit e aprirò la pull request."`
4. **Revisione della documentazione durante le Sprint Review**
   Durante la **Sprint Review**, oltre a mostrare la funzionalità implementata, la documentazione correlata deve essere parte della dimostrazione. Questo permette agli stakeholder di verificare che le informazioni tecniche siano chiare, comprensibili e complete. Se ci sono suggerimenti o richieste di

### Automatizzare la generazione e la validazione

L'automazione è un aspetto cruciale dell'approccio **Documentation as Code**, e la **developer platform** gioca un ruolo chiave nel garantire che la documentazione venga generata e validata automaticamente. L'adozione di pipeline CI/CD dedicate alla documentazione assicura che ogni modifica venga gestita e pubblicata in modo accurato e tempestivo, riducendo il rischio di errori manuali e migliorando l'efficienza del team.

Grazie alla Piattaforma di Sviluppo ed Automazione, il processo di generazione, validazione e distribuzione della documentazione può essere completamente automatizzato. Di seguito sono riportati i principali passaggi per sfruttare al meglio una developer platform nell'automazione della documentazione.

**Attività principali per l'automazione della documentazione nella developer platform:**

1. **Configurazione delle pipeline CI/CD per la documentazione**
   La prima fase dell'automazione consiste nell'integrare la generazione e la validazione della documentazione all'interno delle pipeline CI/CD della developer platform. La piattaforma può essere configurata per eseguire automaticamente una serie di task ogni volta che viene effettuato un commit nel repository, come ad esempio:

   - Generazione della documentazione a partire dai commenti nel codice (es. usando strumenti come **Swagger** per API documentation o **JSDoc** per JavaScript).
   - Validazione della correttezza della sintassi della documentazione (es. **Markdown linting**).
   - Verifica della completezza della documentazione e controllo dei link (es. verificare che non ci siano link interrotti o sezioni mancanti).

   **Esempio**: In un repository per un'API REST, si può configurare la pipeline CI/CD della developer platform per generare automaticamente la documentazione API da commenti nel codice usando Swagger. La pipeline esegue quindi il linting per verificare che la documentazione sia ben formattata, segua gli standard definiti e non contenga errori.
2. **Generazione automatica della documentazione**
   Ogni volta che viene creato un commit o una pull request, la pipeline CI della developer platform può eseguire la generazione della documentazione. La documentazione può essere creata automaticamente utilizzando strumenti che estraggono informazioni dai commenti del codice, come **JSDoc**, **Sphinx** o **Swagger**, per documentare API, librerie o framework.

   **Esempio**: Supponiamo che uno sviluppatore aggiunga una nuova funzionalità API nel codice sorgente. Quando il commit viene eseguito, la pipeline CI della developer platform avvia automaticamente il processo di generazione della documentazione API usando Swagger, basandosi sui commenti inseriti dallo sviluppatore direttamente nel codice. Il risultato è un documento aggiornato che descrive l'endpoint, i parametri, le risposte e gli errori della nuova API.
3. **Validazione automatica della documentazione**
   Dopo la generazione, la developer platform può eseguire la **validazione** automatica della documentazione, sia di quella generata automaticamente a partire dal codice sorgente che di quella redatta dal team di sviluppo, tramite strumenti di linting e altri controlli di qualità. Questi controlli possono includere:

   - **Linting del Markdown**: per garantire che il formato del documento sia corretto e coerente.
   - **Controllo dei link**: per assicurarsi che tutti i link nella documentazione siano validi e non interrotti.
   - **Verifica della completezza**: per assicurarsi che tutte le funzionalità, endpoint o moduli del software siano correttamente documentati.

   **Esempio**: Dopo aver generato la documentazione, la pipeline CI della developer platform esegue un controllo automatico sui file Markdown per assicurarsi che seguano il formato corretto. Se ci sono errori di sintassi, link non validi o altre anomalie, il sistema genera automaticamente un report di errore che blocca la pull request finché non vengono risolti.
4. **Automatizzazione del deploy della documentazione**
   Oltre alla generazione e validazione, la developer platform può essere configurata per gestire automaticamente il **deploy** della documentazione sulla piattaforme di distribuzione  della documentazione. Questo significa che ogni modifica approvata al codice porta automaticamente a un aggiornamento pubblico della documentazione.

   **Esempio**: Una volta che una pull request viene fusa nel branch principale (`main` o `master`), la pipeline CI esegue automaticamente il deploy della documentazione aggiornata sulla piattaforma dedicata ai team di sviluppo. Questo assicura che la documentazione sia immediatamente accessibile agli utenti o agli sviluppatori interni senza dover eseguire passaggi manuali.
5. **Integrazione dei report nella developer platform**
   La developer platform può essere configurata per generare **report automatici** che segnalano il successo o il fallimento dei processi di generazione e validazione della documentazione. Questi report vengono inviati direttamente al team tramite notifiche (ad esempio, via Slack, email o altre integrazioni) e possono essere visualizzati direttamente nella dashboard della piattaforma.

   **Esempio**: Dopo l'esecuzione della pipeline, un report viene generato e visualizzato nella dashboard della developer platform, indicando se la documentazione è stata generata e distribuita correttamente o se ci sono stati problemi. Se viene rilevato un errore, il report evidenzia i problemi (come link non validi o errori di formattazione) e consente al team di intervenire rapidamente.

### Scegliere formati di documentazione semplici e scalabili

L'adozione del formato testuale **Markdown** consente di mantenere la documentazione leggera, flessibile e facilmente gestibile tramite version control. Markdown è un formato di testo semplice che può essere reso in modo leggibile sia nella sua forma raw, sia su piattaforme che offrono rendering HTML (come **GitHub**, **GitLab**, **Read the Docs**, e **GitHub Pages**) e, nella soluzione adottata dall'Amministrazione, sul portale della documentazione reso disponibile ai team di sviluppo nell'ambito della Piattaforma di Sviluppo e Automazione basato su Backstage. Questo lo rende particolarmente adatto per la documentazione tecnica, poiché riduce la complessità e il sovraccarico introdotto da strumenti o formati più sofisticati, e garantisce la manutenibilità a lungo termine della documentazione.

L'utilizzo di Markdown consente di:

- **Gestire facilmente il versionamento**: Le modifiche ai file di testo Markdown sono facilmente tracciabili in Git, e possono essere revisionate tramite pull request o altri meccanismi di code review.
- **Facilitare la collaborazione**: Chiunque nel team, indipendentemente dagli strumenti usati, può contribuire alla documentazione con un semplice editor di testo, senza dover imparare tecnologie o formati complessi.
- **Rendere la documentazione accessibile su diverse piattaforme**: Il formato Markdown è supportato da molteplici piattaforme, sia per la lettura locale che per la pubblicazione online.

#### Esempio di utilizzo del formato Markdown:

Supponiamo di dover documentare una nuova API `/users` che permette di ottenere una lista di utenti. Creare il file `api/users.md` in formato Markdown per documentare questa funzionalità risulta semplice e intuitivo, garantendo che il file possa essere gestito facilmente tramite Git e visualizzato in maniera leggibile su qualunque piattaforma di hosting di documentazione.

**Esempio di documento API in Markdown** (`doc/api/users.md`):

```markdown
# API `/users`

Questa API consente di ottenere la lista degli utenti presenti nel sistema.

## Endpoint
`GET /users`

## Parametri

| Parametro   | Tipo   | Descrizione                              |
|-------------|--------|------------------------------------------|
| `page`      | int    | (Facoltativo) Numero della pagina         |
| `limit`     | int    | (Facoltativo) Numero di risultati per pagina |

## Risposta

La risposta sarà un oggetto JSON contenente la lista degli utenti.

### Esempio di richiesta

curl -X GET "https://api.esempio.com/users?page=1&limit=10"

### Esempio di risposta

{
  "users": [
    {
      "id": 1,
      "nome": "Mario Rossi",
      "email": "mario.rossi@example.com"
    },
    {
      "id": 2,
      "nome": "Luca Bianchi",
      "email": "luca.bianchi@example.com"
    }
  ],
  "page": 1,
  "limit": 10
}

### Codici di errore

| Codice | Messaggio              | Descrizione                  |
|--------|------------------------|------------------------------|
| `404`  | Not Found              | Nessun utente trovato         |
| `500`  | Internal Server Error   | Errore interno del server     |

```

**Perché usare Markdown?**

- **Leggibilità raw**: Anche senza l'uso di un visualizzatore, il file può essere letto e compreso direttamente da chiunque apra il file in un editor di testo.
- **Compatibilità con Git**: La struttura di testo semplice permette una gestione agevole del versionamento tramite Git. Ad esempio, in caso di modifiche, si può vedere chiaramente cosa è stato aggiunto o modificato all'interno del file tramite i normali strumenti di differenziazione (diff).
- **Visualizzazione su piattaforme di hosting**: Quando questo file viene caricato su GitHub o GitLab, sarà automaticamente renderizzato in HTML, mostrando una versione formattata e navigabile del documento senza necessità di ulteriori conversioni o strumenti di terze parti.

**Integrazione con altre piattaforme**:

- **GitHub Pages**: La documentazione scritta in Markdown può essere facilmente pubblicata utilizzando GitHub Pages, convertendo automaticamente i file `.md` in pagine web leggibili.
- **Read the Docs**: Se il progetto è ospitato su **Read the Docs**, i file Markdown verranno automaticamente integrati e resi in HTML, consentendo una navigazione strutturata e professionale.

In questo modo, l'adozione di Markdown semplifica la gestione, la collaborazione e il deploy della documentazione, garantendo flessibilità e scalabilità per l'intero team di sviluppo.

### Scrivere documentazione chiara e concisa

Una buona documentazione deve essere **chiara**, **concisa** e facile da comprendere sia per gli sviluppatori esperti che per i nuovi membri del team o utenti esterni. Evitare linguaggio prolisso o tecnico non necessario è essenziale per mantenere la documentazione accessibile e utile. Ogni sezione dovrebbe rispondere chiaramente a domande specifiche senza lasciare spazio a interpretazioni ambigue.

Per garantire che la documentazione sia comprensibile:

- **Usa frasi brevi e dirette**.
- **Evita l'uso di gergo tecnico** a meno che non sia strettamente necessario, e fornisci spiegazioni quando usi termini specifici.
- **Sii esplicito e preciso**: descrivi esattamente cosa fa una funzionalità o un'API, senza lasciare che l'utente debba interpretare.

#### Esempio di buona documentazione di una API

Un esempio di documentazione chiara e concisa per un endpoint API è stato rappresentato nel punto precedente.

#### Esempio di cattiva documentazione di una API

```markdown
### Funzionalità API per l'interrogazione degli utenti

La presente API è stata sviluppata per permettere di ottenere una lista di tutti gli utenti che esistono nel nostro sistema in un dato momento. Questa API utilizza il metodo GET e può essere utilizzata con diversi parametri opzionali, che modificano il comportamento della richiesta. La chiamata all'API è progettata per essere flessibile e per supportare varie operazioni di recupero dei dati degli utenti, a seconda delle necessità operative che l'utente finale potrebbe avere.

#### Metodo
L'API utilizza il metodo GET per recuperare i dati relativi agli utenti. È importante notare che questo metodo può essere chiamato senza alcun parametro, nel qual caso restituirà un insieme di utenti predefinito. In alternativa, si possono fornire parametri per filtrare e ordinare i risultati in base alle esigenze.

`GET /users`

#### Parametri accettati dalla chiamata
Questa API accetta i seguenti parametri. Ogni parametro deve essere correttamente formattato e incluso nella query string:

- **page**: Si tratta di un numero intero che rappresenta la pagina da visualizzare, ma è opzionale. Se non viene fornito, verrà usato il valore predefinito.
- **limit**: Numero massimo di risultati per pagina. Anche questo è opzionale.

#### Risposta attesa dalla chiamata all'API
La risposta fornita dall'API sarà in formato JSON. Essa includerà una lista di oggetti che rappresentano gli utenti recuperati dalla chiamata. La struttura della risposta può variare in base ai parametri forniti.

{
  "users": [
    {
      "id": 1,
      "nome": "Mario Rossi",
      "email": "mario.rossi@example.com"
    },
    {
      "id": 2,
      "nome": "Luca Bianchi",
      "email": "luca.bianchi@example.com"
    }
  ],
  "pagina": 1,
  "totale_utenti": 1000
}

#### Codici di stato HTTP
In caso di errore, l'API restituirà un codice HTTP indicativo del problema riscontrato. Ecco alcuni esempi:

* 404: Utente non trovato.
* 500: Errore interno del server.

```

##### Problemi evidenziati in questo esempio

1. **Linguaggio troppo vago e prolisso**:

   - L'introduzione è prolissa e poco chiara. Espressioni come *"modifica il comportamento della richiesta"*, *"flessibile e per supportare varie operazioni"* sono vaghe e non spiegano chiaramente il funzionamento dell'API.
   - L'intera descrizione avrebbe potuto essere più diretta e concisa.
2. **Informazioni inutili o ridondanti**:

   - "Se non viene fornito, verrà usato il valore predefinito" è ripetuto in più punti e non fornisce informazioni aggiuntive utili. Inoltre, non viene indicato **quale sia** questo valore predefinito.
   - La sezione sui parametri non è dettagliata: mancano le descrizioni dei valori predefiniti, dei limiti numerici e di eventuali validazioni.
3. **Mancanza di esempi utili**:

   - Non viene fornito un esempio di richiesta con parametri concreti, il che renderebbe la comprensione più facile.
   - Non viene menzionata la struttura dell'errore nella risposta, né quali errori possono verificarsi oltre ai codici HTTP menzionati (ad esempio, mancanza di parametri obbligatori o formattazione errata).
4. **Struttura debole e poco visiva**:

   - L'utilizzo delle liste non strutturate per i parametri è meno chiaro rispetto a una tabella, che risulterebbe più leggibile.
   - La risposta JSON manca di spiegazioni o di contesto, come la descrizione dei campi inclusi nella risposta.
5. **Errori di traduzione e incoerenza nei termini**:

   - Nella risposta, viene usato "pagina" al posto di "page", rompendo la coerenza con i parametri.

##### Come migliorare questo esempio

- **Sintetizzare e semplificare** la descrizione per renderla più diretta e comprensibile.
- **Aggiungere dettagli concreti** per i parametri, come i valori predefiniti e i limiti, eliminando informazioni ridondanti.
- **Includere esempi pratici** di richieste e risposte per rendere la documentazione più facile da seguire.
- **Organizzare le informazioni in modo visivo**, utilizzando tabelle per i parametri e i codici di errore.
- **Mantenere coerenza** nei termini usati per evitare confusione tra diverse lingue o convenzioni.

### Utilizzare template standardizzati

L'uso di template per diversi tipi di documenti (ad esempio guide utente, documentazione API, guide di installazione) può migliorare la coerenza e l'efficienza nella creazione dei documenti. I template aiutano anche a mantenere uno standard di qualità, assicurando che tutte le informazioni necessarie siano incluse.

### Favorire il feedback continuo

È importante creare canali di comunicazione per permettere agli utenti (interni ed esterni) di fornire feedback sulla documentazione. Questo può avvenire tramite issue aperte sul repository o strumenti di collaborazione. Il feedback è essenziale per migliorare costantemente la qualità e l'utilità della documentazione.

Incorporare queste **best practice** nel flusso di lavoro quotidiano assicura che la documentazione rimanga un asset vivo, utile e allineato con l'evoluzione del software. La documentazione continua, esattamente come il codice, richiede disciplina, collaborazione e strumenti adeguati per essere mantenuta nel tempo.
