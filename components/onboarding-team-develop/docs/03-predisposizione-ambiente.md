# Predisposizione dell'Ambiente di Sviluppo

## Setup degli Strumenti di Sviluppo

L'ambiente prevede l'integrazione e la configurazione di una serie di strumenti che coprono l'intero processo di sviluppo, dalla scrittura del codice fino al deployment.

La struttura dell'ambiente di sviluppo sicuro è documentata in [Architettura dell&#39;ambiente di sviluppo centralizzato](https://backstage-devel.k8s01.sidt.local/docs/default/component/ambiente-sviluppo-sicuro-architettura-ambiente); gli utenti devono verificare di poter accedere agli strumenti per cui è stata data l'autorizzazione ed impostare i collegamenti nella propria postazione di lavoro. A cura degli amministratori dell'Ambiente di Sviluppo è la predisposizione delle utenze e delle eventuali ulteriori infrastrutture necessarie - sia per l'esecuzione degli ambienti applicativi (database, cluster kubernetes, etc.) che per il supporto allo sviluppo (ulteriori istanze di runner di pipeline, istanze di scala per componenti GitLab / Rancher / Nexus / altri).

Ogni postazione di sviluppo deve disporre di risorse computazionali sufficienti per eseguire gli strumenti di sviluppo in modo efficiente; potenzialmente dovrebbero poter essere in esecuzione contemporanea diversi container con i microservizi propedeutici all'attività di sviluppo locale. È sempre possibile puntare alle installazioni nell'ambiente di sviluppo nel caso in cui l'esecuzione locale non sia possibile.

Oltre agli strumenti che fanno parte dell'ambiente di sviluppo sicuro in forma di web app, l'ambiente richiede alcuni software come un IDE, un client locale per git, ed altri strumenti specifici per ciascun progetto (Java Development Kit, nodejs, etc.). Ogni software deve essere installato e configurato secondo le best practices di sicurezza e performance.

Ogni progetto deve avere risorse dedicate assegnate in base alle esigenze specifiche. Ciò include l'allocazione di spazio su disco per i repository, capacità computazionale per eseguire le pipeline, e risorse di rete per garantire una connessione sicura e veloce tra gli strumenti e i team di sviluppo.

## Configurazione dei Repository

Questo include la struttura del repository, la nomenclatura utilizzata, e le politiche di accesso e controllo delle versioni. Ogni progetto è organizzato secondo una struttura predefinita che riflette la suddivisione logica del sistema in moduli o componenti.

Per maggiori informazioni sulla configurazione dei repository si veda il capitolo apposito di [Architettura dell&#39;ambiente di sviluppo centralizzato](https://backstage-devel.k8s01.sidt.local/docs/default/component/ambiente-sviluppo-sicuro-architettura-ambiente/04-gestione-repository/).

## Integrazione con la CDPx

Ogni progetto dispone di pipeline CI/CD personalizzate, configurate per eseguire automaticamente tutte le fasi del ciclo di vita del software, dalla build al deployment. Le pipeline includono step per l'esecuzione dei test, l'analisi statica del codice, e la gestione dei secret e delle configurazioni.
Le variabili d'ambiente, i file di configurazione, e i secret necessari per l'esecuzione delle applicazioni sono gestiti in modo centralizzato, utilizzando strumenti come Helm e Kubernetes Secrets. Nel repository "k8sconfigrepo" sono contenute le configurazioni e le automazioni infrastrutturali per ciascun componente.

Le pipeline possono essere attivata automaticamente su eventi specifici (es. push su una branch) o manualmente per consentire maggiore controllo su operazioni critiche come i deploy in produzione.
