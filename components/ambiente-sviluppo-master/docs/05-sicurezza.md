# Sicurezza dell'ambiente

La configurazione di sicurezza dell'ambiente di sviluppo è orientata a proteggere il patrimonio intellettuale e garantire l'integrità del software.

## Autenticazione e autorizzazione

Il sistema di autenticazione e autorizzazione è progettato per garantire che solo gli utenti autorizzati possano accedere e modificare il codice sorgente, ed accedere alle funzionalità del pannello dashboard CDP.

Gli utenti accedono al repository tramite un sistema SSO integrato con LDAP, che centralizza la gestione delle credenziali. Questo facilita l'accesso e migliora la sicurezza riducendo il numero di password che gli utenti devono gestire.

Gli accessi sono gestiti tramite RBAC, assegnando permessi specifici ai ruoli utente come descritto al capitolo precedente. Questo assicura che ogni utente abbia accesso solo alle risorse necessarie per il proprio lavoro.

Qualora si ritenessero opportune maggiori garanzie sull'identità degli utenti dell'ambiente di sviluppo sicuro si potrà, in una fase futura, considerare l'adozione dell'autenticazione a più fattori, sia per l'accesso VPN che per l'accesso SSO tramite LDAP.

## Crittografia e protezione dei dati

La protezione dei dati è garantita attraverso l'uso di tecniche di crittografia avanzate e politiche di gestione dei dati. Tutte le comunicazioni tra gli utenti e il repository GitLab sono crittografate utilizzando il protocollo HTTPS, prevenendo intercettazioni e accessi non autorizzati durante il trasferimento dei dati.

I dati memorizzati nel repository, inclusi i file di codice e i documenti associati, sono crittografati utilizzando algoritmi di crittografia robusti. Questo assicura che anche in caso di accesso non autorizzato ai server, i dati rimangano protetti. La stessa logica viene applicata anche ai database, persistent volume, e qualunque altra area di memorizzazione in cui l'ambiente di sviluppo va a persistere dati.

All'interno di GitLab è disponibile uno strumento di Secret Detection in grado di avvisare gli amministratori dell'istanza se qualche sviluppatore ha inavvertitamente persistito con un commit delle credenziali (password, api key, etc.) in modalità non sicura. Questa funzionalità aggiunge un ulteriore passaggio di verifica mirata che contribuisce alla solidità complessiva dell'infrastruttura.

È anche possibile integrare strumenti di terze parti, gratuiti o a pagamento, per effettuare controlli simili con regole più versatili, ad esempio assicurando la presenza di header nei file sorgente contenenti le informazioni di licenza.

## Monitoraggio e logging

Il monitoraggio continuo e il logging dettagliato delle attività nell'ambiente di sviluppo sono fondamentali per rilevare e rispondere tempestivamente a potenziali minacce alla sicurezza. Gli strumenti di monitoraggio come Prometheus e Grafana sono utilizzati per tenere traccia delle metriche di sistema e delle performance. Questo aiuta a identificare anomalie che potrebbero indicare un tentativo di intrusione o altri problemi di sicurezza.

NeuVector e Rancher sono impiegati per il monitoraggio della sicurezza dei container e delle comunicazioni di rete all'interno dell'ambiente Kubernetes, rilevando e segnalando vulnerabilità o comportamenti sospetti, e possono integrare le analisi sul codice "statico" già effettuate in fase di sviluppo.

Le attività degli utenti, inclusi gli accessi, le modifiche al codice e le configurazioni, sono registrate in log dettagliati. Questi log sono memorizzati in un sistema centralizzato e sono accessibili solo a personale autorizzato. Elasticsearch e Kibana sono utilizzati per aggregare e visualizzare i log, facilitando l'analisi e l'investigazione di incidenti di sicurezza.

Per via del funzionamento della tecnologia Git, nella configurazione predefinita ogni commit è firmato dall'autore in modalità dichiarativa. Qualora si desiderasse incrementare il livello di garanzia di corrispondenza tra l'autore di un commit e la vera identità dell'utente che lo ha prodotto si potrà valutare, in una fase futura, l'introduzione dei commit firmati digitalmente.

## Conformità normativa

La conformità normativa è importante per operare in modo legale e etico, rispettando le leggi e i regolamenti applicabili in materia di sicurezza e protezione dei dati.

Il sistema di gestione della sicurezza è progettato per essere conforme ai principali standard e regolamenti internazionali, come il Regolamento Generale sulla Protezione dei Dati (GDPR), la normativa ISO/IEC 27001 sulla gestione della sicurezza delle informazioni, e le linee guida OWASP per la sicurezza del software.

***Pur richiamando l'importanza della conformità alle normative mano a mano vigenti, si rimanda ai singoli contratti di fornitura per approfondimenti sui vincoli e sulle relative garanzie.***
