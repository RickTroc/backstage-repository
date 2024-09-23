# Procedura di Change Management

In questo capitolo sono fornite le informazioni fondamentali sulle linee guida per l'attivazione del processo di Change Management.

## Obiettivi e contesto di riferimento

I servizi di "Service Management" sono organizzati e strutturati secondo un approccio process-driven, in cui la complessa struttura organizzativa/operativa è scomposta in processi integrati e correlati tra loro in accordo con le best practices ITIL4, con l'obiettivo di migliorare la qualità dei servizi IT, ridurre i costi di erogazione dei servizi e allineare i servizi IT con le esigenze correnti e future dell'Amministrazione.

In questo ambito si colloca il processo di Change Management finalizzato a una gestione efficace ed efficiente della gestione dei cambiamenti (Change).

## Tipologia di Change

ITIL v4 classifica i cambiamenti in diverse categorie, ognuna delle quali richiede un approccio di gestione diverso. Di seguito sono riportate le categorie di cambiamento configurate anche nello strumento di tracciatura HP Service Manager:

- **Stardard Change:** Sono modelli di Change definiti e pre- approvati di basso rischio. Questi Change vengono considerati come eventi di routine e/o come normali Richieste di Servizio.
- **Normal Change:** Cambiamenti che richiedono una valutazione individuale in termini di impatto e rischio e devono essere approvati da un Change Advisory Board (CAB).Questa tipologia di Change viene discussa al CAB, ne viene assegnata priorità e ne viene valutato il rischio facendo riferimento al documento di "Risk Impact Assessment" precompilato dal change owner.
- **Emergency Change:** Change che devono essere implementati il prima possibile, necessari al ristabilimento delle condizioni necessarie per il mantenimento del servizio o dei Livelli di Servizio. È un change che deve avere un assessment e processo autorizzativo veloce in quanto esiste un chiaro e certo rischio con relativo impatto imminente.
- **Urgent change**: Normal change la cui applicazione assume carattere di urgenza.

Ad oggi le attività di gestione dei Change riguardano:

- Componenti hardware
- Software di base
- Strumenti di utilità
- Applicazioni specifiche

In generale tutte le attività di gestione delle modifiche sono realizzate in linea con le esigenze operative dell'Amministrazione e sono state identificate le seguenti tipologie:

- **Evolutiva:** Change legato ad un'evoluzione di una componente del sistema o alla nascita di una nuova componente
- **Correttiva:** Change legato a una correzione di una qualsiasi componente del sistema
- **Migliorativa:** Change legato a interventi su componenti del sistema per performance e tuning (esempio: ricreazione indici su tabelle del db per ottimizzazione degli accessi)
- **Adeguativi:** Change legato ad un adeguamento a nuove necessità (esempio: modifica alla configurazione del pix per abilitazione nuove utenze)
- **Localizzata:** Assistenza applicativa o sistemistica (es. lancio di un batch)

Si riporta di seguito una tabella di corrispondenza tra la classificazione di un Change e la categoria prevista per il cliente:

| Tipologia change per MIT | Classificazione   |
| ------------------------ | ----------------- |
| Evolutiva                | Normal Change    |
|                          | Urgent Change     |
| Correttiva               | Emergency Change |
| Migliorativa             | Standard Change   |
| Adeguativa               |                   |
| Localizzata              |                   |

Tabella 2 -- Corrispondenza tra la classificazione e la categoria del Change

## Priorità e valutazione di impatto e rischio di un change

La priorità di un Change è determinata combinando l\'urgenza del Change
con la sua importanza, l\'impatto previsto e, non da ultimo, la
relazione con gli altri Change previsti. La definizione delle priorità
aiuta a garantire che i cambiamenti più critici siano affrontati per
primi. La definizione delle priorità viene evidenziata nella tabella
seguente:

| Priorità       | Descrizione                                                                                                                                      | Esempio                                                                                                                                                                                                             |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bassa** | Cambiamenti che hanno un impatto minimo e non<br />sono urgenti possono essere implementati quando <br />le risorse sono disponibili            | Ottimizzazioni minori, modifiche estetiche,<br />miglioramenti che non influenzano <br />immediatamente il servizio. Quale ad es.<br />possono essere un passaggio di release, <br />o una manutenzione schedulata. |
| **Media** | Non cè urgenza, ma il cambiamento non dovrebbe<br />essere comunque prorogato. In questo caso <br />vengono assegnate le necessarie risorse | Miglioramenti delle funzionalità del sistema,<br />aggiornamenti di routine che migliorano <br />l'efficienza.                                                                                                     |
| **Alta**  | Riguarda la risoluzione di un problema che coinvolge<br />pesantemente la soddisfazione dei Livelli di Servizio, <br />o un cambiamento urgente. | Risoluzione di un bug critico che causa<br />un'interruzione del servizio, patch di sicurezza <br />urgenti.                                                                                                        |

Tabella 3 -- Priorità e descrizione

La valutazione del rischio e dell'impatto del Cambiamento viene
determinata attraverso la compilazione di un documento di "Risk Impact
Assessment" e viene valutata all'interno del CAB.

Il Risk Impact Assessment si basa su due aspetti:

- la probabilità che si verifichi un rischio
- il potenziale impatto negativo di un rischio qualora si verifichi.

Di seguito si riportano due tabelle che definiscono i livelli di impatto
e rischio.

| **Impatto**   | **Descrizione**                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Low**       | Il cambiamento richiede poco lavoro e un basso impatto sui servizi in esercizio                                                                                                                                                                                                                                                                                                                                       |
| **Medium**    | Il cambiamento richiede un normale lavoro e avrà un impatto medio sui servizi in esercizio e quindi sui Livelli di Servizio.                                                                                                                                                                                                                                                                                         |
| **High**      | Il cambiamento richiede lavori complessi che avranno un impatto significativo sui servizi in esercizio e quindi sui Livelli di Servizio. Il cambiamento e le modalità di intervento vengono discussi in una riunione del CAB, con le rappresentanze di tutte le strutture coinvolte e si organizzeranno delle apposite war-room per poter gestire il change e intervenire tempestivamente in caso di problemi        |
| **Very High** | Il cambiamento richiede lavori complessi che avranno un impatto significativo su tutti i servizi in esercizio e quindi sui Livelli di Servizio. Il cambiamento e le modalità di intervento vengono discussi in una riunione del CAB, con le rappresentanze di tutte le strutture coinvolte e si organizzeranno delle apposite war-room per poter gestire il change e intervenire tempestivamente in caso di problemi |

Tabella 4 -- Tipologie impatto

Le tipologie di rischio vengono descritte nella tabella seguente:

| **Rischio**   | **Descrizione**                                                                                                                                                                     |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **No Risk**   | Il cambiamento richiede poco lavoro e un basso rischio impatto sui servizi in esercizio                                                                                                   |
| **Low**       | Il change comporta rischi bassi su una minima parte dei servizi erogati, rischio accettabile                                                                                              |
| **Some**      | Il change comporta rischi bassi su più servizi erogati, rischio accettabile                                                                                                              |
| **Moderate**  | Il change comporta rischi rilevanti su più servizi erogati, e deve essere approvato dal CAB                                                                                              |
| **High**      | Il change comporta alto rischio su più servizi erogati, e deve essere approvato dal CAB                                                                                                  |
| **Very High** | Change con rischi sui servizi molto alti. Deve essere valutata al CAB la possibilità di ridurre il rischio implementando azioni di mitigazione e conseguentemente approvato e monitorato |

Tabella 5 -- Tipologie rischio

Una volta identificati e valutati i rischi, vengono sviluppate delle strategie di mitigazione. Le strategie di mitigazione sono azioni che
possono essere intraprese per ridurre la probabilità o l'impatto di un rischio. Alcune strategie di mitigazione possono includere:

- **Evitare il cambiamento**: se il rischio fosse troppo alto, il cambiamento potrebbe essere annullato o posticipato.
- **Minimizzare il cambiamento**: se il cambiamento è necessario, può essere progettato per ridurre al minimo l'impatto del rischio.
- **Controlli preventivi**: è possibile mettere in atto controlli per prevenire il verificarsi del rischio, come test e formazione.
- **Controlli investigativi**: è possibile mettere in atto controlli per rilevare il rischio qualora si verifichi, come sistemi di monitoraggio e registrazione degli eventi.

## Fasi di un change

Le fasi del change sono diverse a seconda del tipo di change.

- **Normal ed urgent change:**
  - Change logging (Apertura del change)
  - Change review (Revisione del change)
  - Change approval (Approvazione del change)
  - Change implementation (Implementazione del change)
  - Change closure (Chiusura del change)
- **Change standard ed emergency**:
  - Change logging (Apertura del change)
  - Change implementation (Implementazione del change)
  - Change Closure (Chiusura del change)

## Linee guida per la gestione nuovo Change

A seguito di un nuovo change il Change owner dovrà:

- Compilare il RiskImpactAssessment per la valutazione del rischio,
  dell'impatto e della categoria del change.
- Predisporre il Runbook
- Aprire il change record sul tool HP/Service Manager, riportando le
  informazioni richieste facendo riferimento al documento di
  Istruzioni operative

Una volta che il change è stato discusso, approvato e pianificato
durante il CAB bisognerà:

- Pianificare se necessaria la war-room con le risorse coinvolte e
  avendo cura di inserire come opzionali i referenti di processo
  attraverso mailbox di processo predefinite
- All'interno della war-room attivare le note nel caso si presentino
  dei problemi per la tracciatura delle azioni intraprese
- Inviare una mail di chiusura attività specificandone l'esito

Nel caso di un change terminato in maniera anomala il change manager
procederà alla schedulazione di un'apposito meeting di "Post
Implementatio Review"

## Linee guida per la gestione di un emergency o urgent change

A seguito di un change urgente e/o di tipo emergency il change owner
dovrà:

- Compilare il RiskImpactAssessment Tool per la valutazione del
  rischio, dell'impatto e della categoria del change.
- Predisporre l'eventuale document di Runbook
- Aprire il change record sul tool HP/Service Manager, riportando le
  informazioni richieste facendo riferimento al documento di
  Istruzioni operative
- Inviare mail ai gruppi predefiniti a seconda delle fasi

  - richiesta di approvazione urgente alle seguenti mailbox di processo:
    richiesta di schedulazione di un CAB/EC straordinario per la
    condivisione e gestione delle approvazioni

Una volta che il change è stato discusso, approvato e pianificato:

- Pianificare se necessaria la war-room con le risorse coinvolte e
  avendo cura di inserire come opzionali i referenti di processo
- All'interno della war-room attivare le note nel caso si presentino
  dei problemi per la tracciatura delle azioni intraprese
- Inviare una mail di chiusura attività specificandone l'esito

Nel caso di un change terminato in maniera anomala il change manager
procederà alla schedulazione di un apposito meeting di "Post
Implementatio Review".
