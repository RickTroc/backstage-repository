# Processi di Promotion

## Ambienti di Promozione

Nel contesto della piattaforma CDP, la promozione degli artefatti software attraverso vari ambienti di sviluppo, collaudo e produzione è gestita in modo automatizzato e controllato. Gli ambienti previsti sono:

* **Ambiente di Sviluppo**: Utilizzato per la scrittura e il test iniziale del codice. In questo ambiente, gli sviluppatori possono eseguire test unitari e di integrazione continua.
* **Ambiente di Collaudo (Staging)**: Un ambiente che replica il più fedelmente possibile l'ambiente di produzione, utilizzato per test end-to-end e test di regressione. È in questo ambiente che vengono effettuate le verifiche tecniche e le approvazioni finali prima della promozione alla produzione.
* **Ambiente di Produzione**: Il contesto operativo finale dove l'applicazione viene utilizzata dagli utenti finali. L'accesso e le modifiche in questo ambiente sono strettamente regolamentati per garantire la stabilità e la sicurezza del sistema.

Ogni ambiente è isolato e ha regole di accesso e di gestione specifiche, conformi alle politiche di sicurezza dell'organizzazione.

## Criteri per la Promotion

La promozione di un artefatto software da un ambiente all'altro nella piattaforma CDP segue criteri rigorosi progettati per garantire la qualità e la sicurezza del software rilasciato. I criteri base, eventualmente specializzati nei singoli contratti di fornitura, sono:

* **Superamento dei Test di Qualità e Sicurezza**: Gli artefatti devono superare tutti i test di qualità (es. test unitari, di integrazione) e di sicurezza (es. SAST, DAST) definiti nelle pipeline CI/CD. Sono presenti controlli come livelli minimi di coverage e vulnerabilità che devono essere superati prima di poter procedere con la promozione.
* **Approvazioni Manuali**: Spesso è richiesta l'approvazione manuale da parte di responsabili tecnici o del team di sicurezza per proseguire con la promozione, specialmente quando si tratta di promuovere in ambiente di produzione.
* **Verifica delle Dipendenze e delle Configurazioni**: Assicurarsi che tutte le dipendenze e le configurazioni necessarie siano soddisfatte nell'ambiente di destinazione. Questo include la verifica delle versioni dei servizi, dei database e delle configurazioni di rete.

## Workflow di Approvazione

Il workflow di approvazione per la promozione del software tra gli ambienti è strutturato per garantire che tutte le modifiche siano attentamente esaminate e convalidate. Il processo, che può essere integrato con dettagli nei singoli contratti, include i seguenti passaggi:

1. **Revisione del Codice**: Prima della promozione, il codice deve passare attraverso un processo di revisione da parte di altri membri del team, utilizzando strumenti di code review integrati come GitLab Merge Request.
2. **Test Completi**: Viene eseguito un ciclo completo di test automatici, che include test di sicurezza, qualità del codice e test funzionali.
3. **Notifica al Team Architetture della disponibilità di una nuova versione**: il PM del progetto notifica al Team di architettura la disponibilità della versione per la promozione; in accordo con il Referente Tecnico dell'Amministrazione, si organizzano le fasi successive.
4. **Approvazione da parte dei Responsabili**: per la promozione oltre la fase di collaudo è necessaria l'approvazione del responsabile tecnico e del team di sicurezza, ad eccezione di specifiche variazioni minori concordate comunque preventivamente con il team sicurezza  (ad es. variazione di immagini/loghi, cambio diciture UI). Spesso è anche prevista una fase di collaudo con una commissione tecnica appositamente istituita dall'Amministrazione; in questo tipo di collaudi vengono verificati interi lotti di modifiche prima di poter procedere con il passaggio in produzione.

Tutte le attività di promozione sono tracciate e registrate per scopi di audit e compliance. Questo include chi ha approvato la promozione, i risultati dei test, e qualsiasi nota o commento aggiuntivo.

## Gestione dell'Approvazione di Sicurezza

In fase di verifica delle segnalazioni da parte del team Sicurezza (sia derivanti da analisi automatizzata del codice, sia da attività di VA/PT) è necessario dare un riscontro a tutte le osservazioni prima di poter procedere con l'approvazione. Il riscontro valido può essere di tre tipi: Risolto, Falso Positivo, Rischio Accettato.

Il riscontro più probabile è il caso in cui, a seguito di una segnalazione, il team di sviluppo riprende la lavorazione del componente per risolvere il problema segnalato, con variazioni di procedura o di configurazione, secondo necessità. Viene annotata la risoluzione del problema nella documentazione di approvazione di sicurezza.

È anche possibile che gli strumenti e le analisi sollevino un'osservazione ma che questa, dopo un'analisi del contesto e del caso, risulti riconducibile ad un falso positivo. In questo caso è necessario integrare nella documentazione di approvazione di sicurezza una breve descrizione della motivazione per cui si ritiene che l'osservazione rappresenti un caso di falso positivo; in questo caso il team di sicurezza può integrare una regola per le future analisi a riduzione di questi casi, che comportano un dispendio di tempo di analisi.

Infine è anche possibile il caso, benché auspicabilmente raro, in cui la segnalazione di sicurezza sia realmente dovuta ad una problematica che comporta un rischio rispetto alle linee guida di standard di sicurezza fissati per l'ambito del componente software in corso di approvazione, ma che non può essere risolta all'interno di un perimetro di vantaggio del rapporto costi/benefici (ad esempio non esaustivo, il cambio di un componente di libreria deprecato richiederebbe una riscrittura inaspettata troppo onerosa). Soprattutto in questo tipo di situazioni deve essere prodotta una documentazione di contesto, simile a quella per i casi di falso positivo, ma che sia in grado di descrivere anche le potenziali manifestazioni dei rischi segnalati, oltre al contesto di valutazione di rischi e benefici dell'approvazione in corso, e dia modo al team sicurezza di decidere se procedere o meno con l'approvazione.

## Rollback e Gestione degli Errori

Nel caso in cui un'operazione di promozione fallisca o si verifichi un problema nell'ambiente di destinazione, la piattaforma CDP è configurata per eseguire un rollback automatizzato. Le politiche di rollback sono progettate per minimizzare l'impatto delle interruzioni e garantire il ripristino rapido dell'ambiente di produzione.

In caso di fallimento di un deploy, il sistema ripristina automaticamente l'ultima versione stabile dell'applicazione utilizzando immagini container precedentemente approvate e memorizzate nel registry. Utilizzando strumenti di monitoraggio dello stato dei replica set e dei deployment, la piattaforma CDP tiene traccia dello stato del sistema in tempo reale. Gli errori o le anomalie rilevate attivano notifiche automatiche agli amministratori di sistema per una risposta rapida.

Per ogni ambiente sono predisposti piani di contingenza che descrivono le azioni da intraprendere in caso di errori critici. Questi piani includono rollback completi del sistema, ripristino di backup, e procedure di comunicazione agli stakeholder. Dal momento che le componenti applicative sono gestite in forma di container stateless, a meno dei persistent volume e dei database, il punto principale di attenzione per queste procedure è costituito dalle modalità per consentire di ripristinare uno stato consistente di database e persistent volume in caso di rollback.
