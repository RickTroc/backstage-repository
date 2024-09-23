# Manuali di Gestione Operativa

I Manuali di Gestione Operativa, uno per ciascuna applicazione o microservizio, sono uno strumento essenziale che fornisce le istruzioni per la gestione quotidiana del modulo applicativo in produzione, con particolare attenzione agli aspetti operativi e tecnici. Sono rivolti principalmente agli operatori IT, ai system administrator e ai DevOps engineer, che devono assicurarsi che l'applicazione funzioni correttamente e che rispetti i requisiti di sicurezza e disponibilità.

Dal momento che buona parte delle operazioni è stata uniformata nella gestione Kubernetes a container, sia per i moduli applicativi di backend che per quelli di frontend, questo documento dovrebbe evidenziare le eventuali particolarità e le criticità specifiche del caso.

## Modello di Documento

Un manuale di gestione operativa dovrebbe coprire questi punti:

* **Topologia dei componenti**: schema dei collegamenti tra i componenti, raggiungibilità di rete, disponibilità dei volumi di archiviazione
* **Procedure di avvio, arresto, riavvio**: checklist delle operazioni e delle modalità di verifica del buon fine delle procedure
* **Monitoraggio e log**: metriche particolari per finalità applicative di data observability, eventuali particolarità delle righe di log
* **Configurazioni**: spiegazione delle impostazioni di configurazione del modulo applicativo. Eventuali particolarità nella gestione dei secret rispetto allo standard infrastrutturale
* **Backup e Ripristino**: eventuali attenzioni particolari per assicurare la consistenza e l'integrità delle copie di backup dei dati del modulo applicativo. Eventuali differenze rispetto allo standard infrastrutturale
* **Troubleshooting**: se opportuno, eventuali indicazioni di massima sull'approccio alla risoluzione dei problemi del modulo applicativo
