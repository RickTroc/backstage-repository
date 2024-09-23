
# Strumenti e Tecnologie

In questo capitolo vengono descritti gli strumenti e le tecnologie necessari per adottare l'approccio  **Documentation as Code** . Questi strumenti consentono di gestire in modo efficiente la documentazione tecnica, mantenendola versionata, automatizzata e integrata nel flusso di sviluppo del software.

## Strumenti per il Versioning

Il versionamento della documentazione è un elemento fondamentale nell'approccio Documentation as Code. Utilizzare un sistema di version control consente di mantenere uno storico delle modifiche, facilitare la collaborazione e assicurare che la documentazione sia sempre allineata con il codice sorgente.

Lo strumento adottato dall'Amministrazione è GitLab, una piattaforma per la gestione di repository Git che offrono, oltre alle funzionalità di base di gestione dei repository del codice di git, funzionalità avanzate come pull request, revisioni, e pipeline di CI/CD integrate per la validazione automatica della documentazione.

### Esempio di flusso di lavoro:

* Creare un branch separato per ogni nuova feature o modifica alla documentazione.
* Usare le pull request per la revisione collaborativa delle modifiche.
* Versionare la documentazione con tag e release, per garantire che ogni versione del software abbia la documentazione corretta associata.

## Editor e IDE consigliati

L'uso di editor e IDE adatti facilita la scrittura della documentazione e l'integrazione nel flusso di lavoro quotidiano degli sviluppatori. Gli editor dovrebbero offrire supporto per i formati di documentazione più comuni (in particolare, Markdown), integrazioni con sistemi di versionamento come Git, e plugin per l'anteprima della documentazione.

### Editor e IDE più utilizzati:

* **Visual Studio Code** : Editor open-source con supporto avanzato per Markdown, Git integrato e numerosi plugin per la gestione della documentazione. Offre l'anteprima in tempo reale di file Markdown e strumenti per l'editing collaborativo.
* **Atom** : Un altro editor open-source, personalizzabile con plugin che supportano Markdown, linting della documentazione e Git.

### Plugin utili:

* **Markdown Preview Enhanced (VS Code)**: Consente di visualizzare l'anteprima in tempo reale dei file Markdown.
* **Office Viewer(Markdown Editor) (VS Code)**: Consente di visualizzare e operare sui file Markdown in modalità WYSIWYG
* **GitLens (VS Code)** : Fornisce informazioni dettagliate su ogni commit legato alla documentazione e ai file versionati.

## Strumenti di automazione e CI/CD

L'integrazione continua (CI) e la distribuzione continua (CD) sono essenziali per automatizzare la generazione, validazione e distribuzione della documentazione. Gli strumenti di automazione aiutano a garantire che la documentazione sia sempre aggiornata, verificata e pubblicata in modo automatico senza interventi manuali.

La piattaforma di sviluppo ed automazione è basata sulla soluzione **CDP (Container Developer Platform)** di **DXC** che gestisce le catene di CI/CD ed i workflow automatizzati per la generazione e la pubblicazione della documentazione a partire dalle operazioni fatte sul repository git di GitLab.

L'integrazione con la piattaforma Backstage preposta ad ospitare la documentazione tecnica è assicurata dal plugin `techdocs-core` di Backstege medesimo che procede all'aggiornamento della documentazione pubblicata in occasione delle merge sul branch `main` o `master`.

### Esempio di automazione:

* Creare una pipeline che esegue il linting della documentazione (ad esempio, tramite  **markdownlint**).
* Automatizzare la generazione di documentazione API usando **Swagger** o **JSDoc**.
* Utilizzare la pipeline CI/CD per distribuire automaticamente la documentazione sulla piattaforma di hosting **Backstages**.

## Formati di documentazione

La scelta del formato di documentazione è essenziale per garantire che i contenuti siano facilmente manutenibili, leggibili e compatibili con gli strumenti di automazione e version control. Dopo un'attenta analisi, il formato scelto per la documentazione tecnica del **SIDT** è **Markdown**, per la sua leggerezza, semplicità e ampia compatibilità. Tuttavia, esistono anche altre alternative valide, che possono essere considerate in specifici contesti.

Sebbene ci siano diverse alternative per la creazione della documentazione, **Markdown** rappresenta la scelta ideale grazie alla sua semplicità, flessibilità e ampia compatibilità con strumenti di version control e piattaforme di automazione. Tuttavia, per progetti più complessi o con requisiti specifici (ad esempio, la generazione automatica di manuali o documentazione API interattiva), l'uso di altri formati come **reStructuredText**, **AsciiDoc** o **YAML/JSON** può essere preso in considerazione.

### Markdown

**Markdown** è un linguaggio di markup leggero, ampiamente utilizzato e supportato, progettato per essere semplice da scrivere e leggere sia in formato raw che quando renderizzato. È il formato ideale per documentazioni tecniche che devono essere manutenute da un team di sviluppatori, grazie alle sue caratteristiche di base:

- **Leggibilità raw**: Anche senza l'ausilio di strumenti di rendering, Markdown è facile da leggere in un semplice editor di testo.
- **Compatibilità diffusa**: Markdown è supportato da piattaforme come **GitHub**, **GitLab**, **Bitbucket**, e da vari strumenti di documentazione come **Read the Docs** o **GitHub Pages**.
- **Facilità di uso**: Le sintassi di base per titoli, elenchi, tabelle, link e immagini sono intuitive e richiedono una curva di apprendimento minima.
- **Versioning e collaborazione**: Markdown si integra perfettamente con sistemi di version control come Git, consentendo una facile gestione delle modifiche e il monitoraggio delle revisioni.

#### Vantaggi specifici di Markdown:

- **Semplicità**: L'essenzialità di Markdown lo rende veloce da scrivere e manutenere.
- **Flessibilità**: Può essere utilizzato per una vasta gamma di documenti, dalle semplici guide utente ai README e alla documentazione API.
- **Estensioni supportate**: Su piattaforme come GitHub e GitLab, è possibile includere estensioni come le tabelle, che non fanno parte delle specifiche originali di Markdown.

### Le alternative a Markdown

Sebbene Markdown sia il formato scelto per la documentazione del SIDT, ci sono altri formati di documentazione che potrebbero essere adatti a situazioni specifiche o progetti con requisiti particolari.

Di seguito una breve panoramica delle alternative:

#### reStructuredText (reST)

**reStructuredText (reST)** è un altro linguaggio di markup testuale, simile a Markdown ma più potente e complesso. È utilizzato principalmente in ambiti dove è richiesta una struttura più rigorosa, come la documentazione di progetti Python o la generazione automatica di documenti tecnici tramite strumenti come **Sphinx**.

- **Vantaggi**:
  - Maggiore potenza e flessibilità rispetto a Markdown, supportando sezioni più complesse, indici e riferimenti incrociati.
  - Ampio utilizzo in progetti **Python** e con **Sphinx**, che genera documentazione HTML o PDF da file reST.
- **Svantaggi**:
  - Curva di apprendimento più ripida.
  - Meno intuitivo e leggibile rispetto a Markdown.

#### AsciiDoc

**AsciiDoc** è un formato testuale di markup che offre una sintassi più robusta rispetto a Markdown, con supporto per la creazione di documenti complessi come libri, articoli scientifici e manuali tecnici. AsciiDoc è particolarmente adatto per progetti che richiedono una documentazione altamente strutturata e formattata.

- **Vantaggi**:
  - Sintassi più potente e avanzata rispetto a Markdown, con supporto per strutture complesse come note, avvisi, riferimenti incrociati, e molto altro.
  - Utilizzato in contesti dove è richiesta la generazione di documentazione PDF o HTML di alta qualità, ad esempio con **Asciidoctor**.
- **Svantaggi**:
  - Più complesso e meno intuitivo per documentazioni semplici.
  - Minore supporto rispetto a Markdown su piattaforme di collaborazione come GitHub e GitLab.

#### YAML/JSON per API

Sebbene non siano formati di documentazione nel senso tradizionale, **YAML** e **JSON** sono ampiamente utilizzati per documentare API tramite strumenti come **Swagger/OpenAPI**. Questi formati strutturati consentono di descrivere le API in modo dettagliato e possono essere utilizzati per generare automaticamente documentazione leggibile e interattiva.

- **Vantaggi**:
  - Struttura formale che permette la validazione e l'automazione della documentazione API.
  - Strumenti come **Swagger** o **Redoc** generano automaticamente documentazione interattiva basata su file YAML o JSON.
- **Svantaggi**:
  - Non sono formati testuali facilmente leggibili come Markdown o reST.
  - Utilizzati principalmente per la documentazione di API e non per guide utente o manuali.
