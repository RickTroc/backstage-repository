# Profili e categorie di accesso

La gestione degli accessi e dei permessi è un elemento cruciale per garantire la sicurezza e l'integrità dell'ambiente di sviluppo. L'utilizzo di sistemi di controllo degli accessi basati su ruoli (RBAC) consente di definire chiaramente i livelli di accesso e i privilegi degli utenti in base alle loro funzioni e necessità.

## Ruoli utente

I ruoli degli utenti sono principalmente individuati all'interno del database LDAP e, per immediata conseguenza, nel KeyCloak interno alla CDP. In LDAP viene configurata l'appartenenza dell'utente ai ruoli che consentono:

* l'accesso ai cluster Kubernetes
* l'accesso a Rancher
* l'accesso come Administrator

Invece all'interno di KeyCloak vengono configurati i gruppi per l'accesso alle singole applicazioni ed ai singoli specifici cluster Kubernetes cui ciascun utente ha diritto ad accedere.

Gli altri strumenti dell'ambiente di sviluppo sicuro (Nexus, Harbor, GitLab) si collegano a KeyCloak o direttamente a LDAP per autenticare gli utenti.

All'interno di GitLab invece ogni utente che ha accesso all'ambiente di sviluppo sicuro con qualunque abilitazione è ricondotto, repository per repository, ad uno dei ruoli predefiniti dello strumento:

* Amministratore: Ha accesso completo a tutte le funzionalità del repository e degli strumenti associati. Gli amministratori sono responsabili della gestione delle configurazioni di sistema, dell'integrazione con altri servizi e della supervisione generale dell'ambiente di repository.
* Sviluppatore: Ha accesso ai repository di cui è membro e può eseguire operazioni di push e merge, creare branch, e gestire le merge request. Gli sviluppatori sono i principali contribuenti al codice e sono coinvolti nel processo di code review.
* Sviluppatore Responsabile (Maintainer): Ha un ruolo simile allo Sviluppatore, ma può compiere operazioni di push sui branch protetti, nei casi in cui questa operazione si renda necessaria.
* Revisore: Ha il compito di esaminare le modifiche al codice attraverso le merge request. I revisori forniscono feedback e approvazioni necessarie per garantire che il codice soddisfi gli standard di qualità e sicurezza. Normalmente le revisioni sono svolte da colleghi di ruolo Sviluppatore, ma in alcuni casi può essere utile un contributo più funzionale e meno tecnico.
* DevOps Engineer: Gestisce le pipeline CI/CD, i deploy, e l'infrastruttura necessaria per eseguire i test automatizzati. Questo ruolo richiede una stretta collaborazione con gli sviluppatori per assicurare che il codice venga rilasciato in modo sicuro e continuo.
* Utente Esterno: Fornitori o collaboratori esterni che necessitano di accedere a specifiche parti del progetto. L'accesso degli utenti esterni è strettamente limitato e monitorato.

## Permessi associati ai ruoli GitLab

I permessi sono configurati in modo granulare per assicurare che ogni ruolo abbia accesso solo alle risorse necessarie per le proprie funzioni, minimizzando i rischi di accessi non autorizzati e potenziali vulnerabilità.

### Permessi degli Amministratori

* Accesso completo a tutte le configurazioni del repository e degli strumenti associati.
* Capacità di creare, modificare, e eliminare repository e gruppi.
* Gestione delle pipeline CI/CD e dei deploy.
* Supervisione della sicurezza e dell'integrazione degli strumenti.

### Permessi degli Sviluppatori

* Creazione e gestione di branch e merge request.
* Esecuzione di push e pull dal repository, tranne che per push su alcuni branch protetti
* Accesso ai log e ai report di build e test.
* Visualizzazione e modifica dei progetti di cui sono membri.

### Permessi degli Sviluppatori Responsabili (Maintainer)

* Gli stessi degli Sviluppatori, con la facoltà di effettuare push anche su branch protetti

### Permessi dei Revisori

* Accesso completo alle merge request per esaminare e fornire feedback.
* Capacità di approvare o rifiutare modifiche al codice.
* Accesso ai report di qualità e sicurezza del codice.

### Permessi dei DevOps Engineer

* Gestione delle pipeline CI/CD, inclusa la configurazione e il monitoraggio.
* Esecuzione di deploy in vari ambienti.
* Accesso ai log di infrastruttura e ai report di sicurezza.
* Capacità di risolvere problemi di build e deploy.

### Permessi degli Utenti Esterni

* Accesso limitato a specifici repository o progetti.
* Capacità di visualizzare e commentare il codice, ma non di eseguire push o merge.
