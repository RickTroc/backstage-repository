# Architettura Applicativa

L'architettura applicativa definisce le componenti principali, le interazioni e i requisiti per l'implementazione del modulo software in questione ed il relativo deploy. Ci si attende una presentazione del progetto software, con declinazioni per microservizi, backend-for-frontend, single page application (SPA), processi batch, etc.

Nella presentazione dell'architettura applicativa è importante avere cura di dettagliare le dipendenze del componente dagli altri, sia dipendenze del flusso dati (quale dei sistemi è autoritativo per quali dati), sia dipendenze cronologiche di eventi.

È in questo documento che si inseriscono inoltre le informazioni di massima sulla configurazione di infrastruttura minimale.

## Modello di Documento

Il documento dovrebbe includere queste sezioni:

* **Diagrammi di architettura**: rappresentano i flussi di interazione funzionale, dati, o sequenze di eventi
* **Descrizione delle componenti**: spiegazione delle singole componenti dell'applicativo, con indicazione delle risorse necessarie per la corretta esecuzione di ciascuna (ove applicabile)
* **Dipendenze**: elenco corredato di breve descrizione di dipendenze da librerie, componenti o sistemi esterni. Includere dettagli su eventuali dipendenze da librerie esterne, servizi o API che devono essere monitorate e mantenute sicure nel ciclo di vita del software.
* **Dimensionamento**: indicazioni sul dimensionamento dei componenti e delle interazioni, secondo la metrica dei function points
* **Configurazioni**: indicazioni sulla configurazione di gateway, nomi di endpoint, configurazioni di infrastruttura minime, protocolli di sicurezza, certificati client (ad es. nella comunicazione con sistemi esterni)
* **Infrastruttura minimale**: indicazioni sulle risorse minime per l'esecuzione del modulo applicativo (ad es. pod Kubernetes, spazio nei volumi, risorse RAM e CPU)
* **Altre eventuali particolarità infrastrutturali**
