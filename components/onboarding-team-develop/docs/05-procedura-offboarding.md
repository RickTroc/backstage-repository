# Procedure di Offboarding

Quando un utente lascia l'organizzazione o cambia ruolo, i permessi sono revocati tempestivamente. Il processo di offboarding include la rimozione di credenziali e l'accesso ai repository. Anche in questo caso la lista degli accessi è mantenuta aggiornata per assicurare che tutte le revoche siano tracciabili e verificabili.

## Revoca degli Accessi

Il processo di offboarding per i membri del team che lasciano il progetto o l'organizzazione è un passaggio fondamentale per mantenere la sicurezza dell'ambiente di sviluppo. La revoca degli accessi è gestita in modo tempestivo e coordinato per prevenire qualsiasi accesso non autorizzato dopo la conclusione del rapporto lavorativo.

Quando un membro del team lascia l'organizzazione o viene assegnato a un altro progetto, il Project Manager deve notificare immediatamente il team di sicurezza IT. Questa notifica avvia il processo di offboarding.

Gli account utente associati al LDAP centrale vengono disabilitati, impedendo l'accesso a tutte le risorse integrate con Single Sign-On (SSO), come GitLab e Keycloak. Gli utenti vengono rimossi dai gruppi di accesso su GitLab, dai cluster Kubernetes tramite Keycloak, e da altri sistemi rilevanti. Tutte le chiavi SSH e i token API associati a ciascun utente uscente vengono invalidati.

Se tutti i membri di un gruppo di sicurezza vengono rimossi, il team di amministrazione infrastrutturale o il team di sicurezza IT possono valutare la rimozione contestuale dell'intero gruppo di sicurezza, così da evitare la persistenza di entità inutili nei sistemi di autenticazione.

## Rimozione delle Credenziali

Le credenziali, che includono password, chiavi di accesso, e token, devono essere rimosse o invalidate per evitare che vengano utilizzate in modo improprio.

Le password degli account disabilitati vengono invalidate immediatamente dopo la disattivazione dell'account, e le chiavi SSH e i token API associati all'utente vengono eliminati dal sistema.

Se l'utente aveva accesso a secret o configurazioni critiche, questi vengono aggiornati e ridistribuiti ai membri rimanenti del team. Questo include la rigenerazione delle chiavi di accesso o delle password condivise per evitare potenziali compromissioni.

## Verifiche Post-Offboarding

L'Amministrazione adotta un approccio di controllo periodico volto a identificare eventuali anomalie o accessi non autorizzati residui.

Ad intervalli regolari il team di sicurezza IT esegue un audit sugli accessi per identificare eventuali anomalie, come tentativi di accesso da parte di account che avrebbero dovuto essere disattivati. Questo audit include una revisione dei log di accesso ai repository Git, ai cluster Kubernetes, e ad altri strumenti critici.

Periodicamente si verifica che le risorse precedentemente assegnate a utenti che hanno lasciato l'organizzazione siano state correttamente deallocate o trasferite ad altri membri del team. Questo controllo aiuta a prevenire l'uso inefficiente delle risorse e a garantire che non rimangano configurazioni inattive o vulnerabili.

La lista degli accessi, mantenuta dal team di sicurezza IT, viene aggiornata e revisionata periodicamente per riflettere correttamente lo stato degli utenti e dei loro permessi. Questa revisione è essenziale per mantenere un controllo accurato e aggiornato su chi ha accesso a quali risorse all'interno dell'ambiente di sviluppo.

## Procedura di Offboarding per i Fornitori

Il processo di offboarding per i fornitori segue un protocollo esteso da quello per i dipendenti, con particolare attenzione alla revoca degli accessi temporanei e al controllo della conformità contrattuale.

Eventuali account temporanei creati per i fornitori vengono disabilitati automaticamente alla fine del contratto o del progetto. Questo include la rimozione di tutti i permessi e l'accesso alle risorse specifiche fornite durante il periodo di collaborazione.

Un audit finale assicura che il fornitore abbia rispettato tutte le clausole di sicurezza e privacy del contratto, inclusa la distruzione di eventuali copie dei dati sensibili. Al termine della collaborazione, tutti i documenti e le risorse utilizzate dal fornitore vengono revisionate e archiviate secondo le policy aziendali. Eventuali strumenti o configurazioni specifiche vengono dismesse o riassegnate internamente.

## Documentazione del Processo di Offboarding

Ogni passo del processo di offboarding deve essere accuratamente documentato per garantire la tracciabilità e la conformità con le politiche aziendali di sicurezza.

Per ogni utente viene utilizzata una checklist standardizzata, elaborata dai capitoli precedenti, che copre tutte le azioni necessarie, dalla revoca degli accessi alla rimozione delle credenziali. Questa checklist viene completata dal team di sicurezza IT e dal team DevOps per assicurare che nessun passaggio venga trascurato.

La documentazione del processo di offboarding, inclusi i log degli accessi e le verifiche finali, viene archiviata in modo sicuro e accessibile solo al personale autorizzato. Questa documentazione è fondamentale per eventuali audit futuri o indagini di sicurezza.

Il processo di offboarding viene rivisto periodicamente per assicurare che sia aggiornato con le migliori pratiche di sicurezza e che rimanga efficace nel proteggere l'ambiente di sviluppo da minacce interne ed esterne.
