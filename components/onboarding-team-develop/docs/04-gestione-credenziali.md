# Gestione delle Credenziali e degli Accessi

## Politiche di Gestione delle Password

La sicurezza degli accessi all'ambiente di sviluppo è garantita da una serie di politiche rigorose per la gestione delle password e delle credenziali. Queste politiche sono progettate per proteggere i sistemi critici e i dati sensibili da accessi non autorizzati e per garantire la conformità con le normative di sicurezza.

Le password devono rispettare criteri di complessità che includono un minimo di 12 caratteri, l'uso di lettere maiuscole e minuscole, numeri e caratteri speciali. Questo requisito riduce il rischio di attacchi di forza bruta o di compromissione delle credenziali.

Le password devono essere aggiornate periodicamente, con una scadenza impostata a 90 giorni. Gli utenti ricevono notifiche per il cambio password prima della scadenza; hanno accesso a un portale self-service per la gestione delle password, che consente loro di cambiarle in qualsiasi momento.

## Single Sign-On (SSO)

L'integrazione del Single Sign-On (SSO) nell'ambiente di sviluppo semplifica la gestione degli accessi, migliorando l'esperienza utente e la sicurezza. Con SSO, gli utenti possono accedere a tutti i sistemi e le applicazioni autorizzate utilizzando un unico set di credenziali, riducendo la necessità di ricordare e gestire più password.

L'ambiente utilizza un server LDAP centralizzato per gestire le identità degli utenti. Questo server è integrato con GitLab, Keycloak (per la gestione dei cluster Kubernetes), e altri strumenti utilizzati dai team di sviluppo. In questo modo, una volta autenticati tramite SSO, gli utenti possono accedere a tutte le risorse necessarie senza ulteriori autenticazioni.

L'accesso alle risorse è gestito tramite ruoli e gruppi definiti in LDAP e Keycloak e sincronizzati con gli altri sistemi. I ruoli determinano i permessi assegnati agli utenti, come la possibilità di eseguire deploy, accedere ai repository, o gestire le configurazioni di sicurezza. Questo approccio centralizzato semplifica la gestione delle autorizzazioni e garantisce la coerenza tra i diversi strumenti.

Per i fornitori che richiedono accesso temporaneo, SSO supporta la creazione di account temporanei con permessi limitati e scadenza automatica. Questo assicura che i fornitori abbiano accesso solo alle risorse strettamente necessarie per il tempo richiesto dal progetto.
