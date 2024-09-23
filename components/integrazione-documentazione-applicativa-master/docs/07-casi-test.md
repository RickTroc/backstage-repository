# Casi di Test

Il documento di specifica dei casi di test è essenziale per garantire che le funzionalità di un sistema o modulo applicativo siano verificate in modo adeguato, fornendo dettagli su come eseguire test per validare i requisiti e la qualità del software. Questo documento è utilizzato principalmente dai team di QA (Quality Assurance) e di sviluppo per progettare, eseguire e monitorare i test, assicurando che il sistema funzioni come previsto.

I casi di test sono generalmente formalizzati a partire dai casi d'uso, e vengono aggiornati mano a mano che procede lo sviluppo dell'applicazione. Sulla base dei casi di test vengono determinati i test di accettazione per la fase di collaudo degli sviluppi.

## Modello di Documento

La descrizione dei casi principali di test, da mantenere allineata con il contenuto dei test automatici nello strumento Cerberus, che deve includere:

* **Denominazione**, codice ed obiettivo del caso di test: descrivere quale funzionalità o comportamento del sistema viene verificato con il test, in linea con i requisiti ed i casi d'uso definiti.
* **Precondizioni**: devono essere soddisfatte prima di eseguire il test. Queste precondizioni potrebbero includere lo stato del sistema, la configurazione dei dati o altre condizioni necessarie.
* **Sequenza di operazioni**: ogni passaggio deve essere chiaro e dettagliato, con eventuali input da fornire e azioni da compiere.
* Dati: elencare i dati di input necessari per l’esecuzione del test, come valori di esempio da inserire o parametri da passare.
* **Risultato atteso**: descrivere il risultato che ci si aspetta dopo l'esecuzione del test. Il risultato atteso deve essere verificabile e deve descrivere lo stato del sistema, i messaggi di conferma, o qualsiasi altra risposta visibile all'utente.
* **Flussi alternativi o Eccezioni**: descrivere eventuali comportamenti alternativi che possono verificarsi, come condizioni di errore o esecuzioni parzialmente riuscite. Questi flussi alternativi possono essere documentati come parte di un caso di test separato o come varianti all’interno dello stesso.
* **Criteri di Successo e di Fallimento**
* **Dipendenze**: eventuali dipendenze tra i casi di test o tra i test e altri sistemi. Ad esempio, un test potrebbe dipendere dall’esecuzione di un altro test o da una configurazione specifica del sistema.
* **Parametri e riferimenti per l'esecuzione del test in Cerberus**
