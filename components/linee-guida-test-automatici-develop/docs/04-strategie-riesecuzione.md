# Strategie di Riesecuzione dei Test

## Test Selettivi Basati sull'Impatto delle Modifiche

I test selettivi basati sull'impatto delle modifiche sono una strategia che consente di eseguire solo i test rilevanti in base alle modifiche apportate al codice. Questo approccio riduce il tempo necessario per eseguire i test e focalizza l'attenzione sui potenziali punti di rottura introdotti dalle modifiche.

Nell'architettura a microservizi dell'Amministrazione questo tipo di vantaggio è ridotto per via della forte modularizzazione delle componenti; tuttavia si menziona ugualmente poiché può essere considerato un punto interessante di evoluzione per ridurre l'effetto collo-di-bottiglia dei test nel flusso di lavoro dello sviluppo quando un repository raggiunge una dimensione considerevole.

Si possono utilizzare strumenti di analisi dell'impatto delle modifiche per identificare quali parti del codice sono state modificate e quali test devono essere rieseguiti; questi strumenti analizzano le dipendenze tra il codice e i test per determinare l'impatto delle modifiche. A questo punto si può configurare la pipeline CI/CD per eseguire solo i test rilevanti in base ai risultati dell'analisi dell'impatto. Questo può includere test unitari, di integrazione ed end-to-end, a seconda delle modifiche apportate.

## Regression Testing

I test di regressione sono essenziali per garantire che le modifiche al codice non introducano nuovi bug o reintroducano bug precedentemente risolti. Nell'ambiente di sviluppo sicuro, i test di regressione comprendono un sottoinsieme di test unitari, di integrazione e end-to-end che coprono le funzionalità chiave dell'applicazione.

Tra gli altri test nel sistema è importante creare e mantenere una suite di test che copra le funzionalità critiche e più utilizzate del sistema. Questa suite deve essere eseguita regolarmente, idealmente ad ogni build o prima di ogni rilascio.

L'esecuzione dei test di regressione deve essere automatizzata per garantire che vengano eseguiti costantemente e senza intervento manuale. Utilizzare strumenti di automazione dei test per configurare e gestire l'esecuzione dei test di regressione.
