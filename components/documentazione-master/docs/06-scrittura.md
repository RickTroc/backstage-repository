# Linee Guida di Scrittura

Per garantire che la documentazione sia sempre chiara, coerente e di alta qualità, è fondamentale seguire linee guida specifiche per la scrittura. Questo capitolo fornisce indicazioni su come utilizzare un linguaggio adeguato, come formattare il contenuto in modo uniforme, e come strutturare gli esempi e il codice per supportare la comprensione del lettore.

## Linguaggio e stile

La scrittura della documentazione tecnica deve essere chiara e accessibile a tutti i membri del team e agli utenti finali. Il linguaggio deve essere formale ma diretto, evitando ambiguità o complessità non necessarie.

### Linee guida per il linguaggio:

- **Semplicità e precisione**: Utilizza frasi semplici e dirette. Evita parole complesse o gergali che potrebbero confondere il lettore. Preferisci un linguaggio che rispecchi il modo in cui un utente leggerà e utilizzerà il prodotto o il servizio.

  **Esempio**:

  - Invece di: "La suddetta funzione potrebbe potenzialmente risultare in un errore"
  - Scrivi: "Questa funzione può causare un errore"
- **Voce attiva**: Usa la voce attiva anziché la passiva per rendere il testo più dinamico e comprensibile. La voce attiva indica chiaramente chi sta eseguendo l'azione.

  **Esempio**:

  - Invece di: "La documentazione deve essere aggiornata dagli sviluppatori"
  - Scrivi: "Gli sviluppatori devono aggiornare la documentazione"
- **Coerenza terminologica**: Usa termini tecnici e parole chiave in modo coerente in tutto il documento. Se utilizzi una terminologia specifica per una funzionalità o un concetto, assicurati di mantenere la stessa denominazione in ogni sezione.
- **Tono neutro e inclusivo**: Evita espressioni colloquiali o informali e usa un linguaggio inclusivo. Mantieni un tono professionale e neutro, adatto a un pubblico tecnico ampio.

  **Esempio**:

  - Invece di: "Ovviamente, chiunque può farlo"
  - Scrivi: "Questo processo può essere seguito da qualsiasi utente"

## Regole per la formattazione

Una formattazione coerente facilita la leggibilità e la navigazione del documento, rendendo più facile per il lettore trovare le informazioni di cui ha bisogno. La formattazione deve essere pensata per supportare la chiarezza e la scansione visiva del testo.

### Linee guida per la formattazione:

- **Titoli e sottotitoli**: Utilizza titoli di livello (`#`, `##`, `###`) per organizzare il contenuto gerarchicamente. Il titolo principale (`#`) dovrebbe essere riservato al titolo del documento, mentre i sottotitoli (`##`, `###`) devono essere utilizzati per suddividere i contenuti in sezioni e sottosezioni.
- **Elenchi puntati e numerati**: Usa gli elenchi puntati (`-`) per elencare informazioni senza una sequenza ordinata, e gli elenchi numerati (`1.`, `2.`) per i passaggi che devono essere seguiti in un ordine specifico.

  **Esempio**:

  ```markdown
  - Passo 1: Configurare l'ambiente.
  - Passo 2: Installare le dipendenze.
  - Passo 3: Avviare il server.
  ```
- **Grassetto e corsivo**: Usa il **grassetto** per enfatizzare concetti o termini chiave, e il *corsivo* per introdurre nuovi termini o enfatizzare parole specifiche.
- **Blocco di codice e inline code**: Utilizza blocchi di codice con tripli backtick (\`\`\`) per mostrare frammenti di codice o comandi complessi, e usa il codice inline con un singolo backtick (\`) per piccoli riferimenti nel testo.

  **Esempio**:

  ```markdown
  Per avviare il server, esegui `npm start` nel terminale.
  ```
- **Tabelle**: Utilizza tabelle per organizzare informazioni strutturate, come parametri di API, proprietà di configurazione, o codici di errore.

  **Esempio**:

  ```markdown
  | Parametro   | Tipo   | Descrizione                              |
  |-------------|--------|------------------------------------------|
  | `page`      | int    | Numero della pagina.                     |
  | `limit`     | int    | Numero di elementi per pagina.           |
  ```

## Best practice per la chiarezza e la concisione

Una documentazione efficace deve essere facilmente comprensibile e concisa. La chiarezza aiuta il lettore a comprendere rapidamente le informazioni, mentre la concisione evita dettagli superflui o ridondanti.

### Linee guida per la chiarezza e la concisione:

- **Scrivi frasi brevi e dirette**: Evita frasi lunghe e complesse. Mantieni le frasi semplici e dirette, così da non sovraccaricare il lettore con informazioni non necessarie.

  **Esempio**:

  - Invece di: "Nel caso in cui si verifichi un errore durante l'installazione, l'utente deve procedere a verificare i file di configurazione"
  - Scrivi: "Se si verifica un errore durante l'installazione, controlla i file di configurazione"
- **Evita ripetizioni**: Evita di ripetere concetti o informazioni che sono già stati trattati. Se un termine o un concetto è stato spiegato in precedenza, fai riferimento a quella sezione piuttosto che riscriverlo.
- **Sii esplicito nei dettagli rilevanti**: Fornisci dettagli sufficienti per completare una procedura o comprendere un concetto, ma non aggiungere informazioni che non sono immediatamente necessarie o che possono confondere il lettore.
- **Usa tabelle e grafici dove opportuno**: Invece di descrivere elenchi complessi o set di dati, utilizza tabelle o grafici per presentare le informazioni in modo più visivo e comprensibile.

## Inclusione di esempi e codice

L'uso di esempi pratici e codice nella documentazione aiuta i lettori a comprendere meglio i concetti astratti e a vedere come le funzionalità possono essere applicate. Gli esempi devono essere chiari, ben formattati e facilmente riproducibili.

### Linee guida per l'inclusione di esempi e codice:

- **Esempi specifici e realistici**: Fornisci esempi che rispecchiano scenari reali e che possono essere facilmente testati dai lettori. Evita esempi astratti o troppo semplici che non aggiungono valore pratico.

  **Esempio**:

  ```markdown
  ### Esempio di richiesta API
  ```bash
  curl -X POST "https://api.esempio.com/prenotazioni" \
  -H "Content-Type: application/json" \
  -d '{
    "utente_id": 123,
    "risorsa_id": 456,
    "data": "2024-09-10T10:00:00Z"
  }'
  ```
- **Fornire contesto per il codice**: Ogni blocco di codice dovrebbe essere accompagnato da una breve spiegazione che ne descriva lo scopo e il contesto in cui va utilizzato. Non inserire mai un blocco di codice senza fornire indicazioni su cosa fa o come deve essere eseguito.

  **Esempio**:

  ```markdown
  Il seguente esempio mostra come effettuare una prenotazione per una risorsa utilizzando l'API:

  ```bash
  curl -X POST "https://api.esempio.com/prenotazioni" \
  -H "Content-Type: application/json" \
  -d '{
    "utente_id": 123,
    "risorsa_id": 456,
    "data": "2024-09-10T10:00:00Z"
  }'
  ```
- **Codice riproducibile**: Gli esempi di codice devono essere facilmente riproducibili dai lettori. Evita di usare valori o variabili ambigui, e includi istruzioni dettagliate per eseguire il codice.
- **Commenti nel codice**: Se il codice è particolarmente complesso, aggiungi commenti per spiegare le sezioni chiave. I commenti non devono essere eccessivi, ma utili per chiarire l'uso di parti meno ovvie del codice.

  **Esempio**:

  ```javascript
  // Controlla la disponibilità della risorsa
  if (risorsaDisponibile) {
      // Effettua la prenotazione
  ```
