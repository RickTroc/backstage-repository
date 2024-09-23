# Casi d'Uso \- Specifiche Funzionali

Un documento di specifica dei casi d'uso è essenziale per descrivere in modo dettagliato come gli utenti interagiscono con il sistema e quali funzionalità devono essere implementate per soddisfare i requisiti operativi.

I casi d'uso forniscono una rappresentazione chiara delle interazioni tra utenti e sistema, consentendo di identificare i flussi principali e alternativi, le precondizioni e i risultati attesi. Questo documento è fondamentale per lo sviluppo, la validazione e i test delle applicazioni.

## Modello di Documento

Ogni caso d'uso dovrebbe includere, facendo riferimento ai principi di modellazione standardizzati in UML, i paragrafi applicabili tra i seguenti:

* **Denominazione ed Obiettivo**: indicazione in breve di cosa si vuole ottenere
* **Attivazione**: indicare se si verifica su condizioni automatiche o su interazione esplicita da parte degli utenti, e la frequenza prevista di utilizzo
* **Attori coinvolti**: con indicazione di attori primari (che iniziano l'interazione) e secondari (coinvolti)
* **Precondizioni**: sono le condizioni che devono essere verificate prima che il caso d'uso possa avere inizio. Definiscono lo stato iniziale del sistema e eventuali requisiti che devono essere soddisfatti per avviare l'interazione
* **Postcondizioni**: descrivono lo stato del sistema dopo che il caso d'uso è stato completato con successo.
* **Flusso principale**: Il flusso principale (anche noto come flusso di eventi o flusso base) descrive i passi principali che devono essere eseguiti affinché il caso d'uso venga completato con successo. Deve essere scritto in modo sequenziale e dettagliato, indicando le azioni dell'attore, le risposte del sistema a ciascuna azione, ed i passaggi successivi fino al completamento dell'obiettivo.
* **Flussi alternativi**: possono verificarsi se si presentano scenari differenti dal flusso principale. Questi flussi coprono casi di errore, eccezioni o scelte alternative che l'utente può fare durante l'interazione.
* **Requisiti non funzionali**: ad esempio richieste di prestazioni, sicurezza, usabilità
* **Diagrammi e grafici, dove applicabile**
