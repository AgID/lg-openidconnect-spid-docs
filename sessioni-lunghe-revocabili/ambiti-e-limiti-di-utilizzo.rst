Ambiti e limiti di utilizzo
===========================

1. Al primo avvio dell’applicazione l’Utente deve essere informato della
   possibilità di utilizzare la sessione lunga revocabile, per mantenere
   un’autenticazione di SPID di livello 1 che consenta all’applicazione
   di ricevere unicamente notifiche o call to action da parte dello SP,
   anche quando l’Utente “non sia presente”;

2. Le applicazioni mobili che fanno uso di sessioni lunghe revocabili
   sono tenute a richiedere all’utente, ad ogni avvio o attivazione, un
   PIN locale oppure un fattore biometrico.

3. In fase di installazione o di prima configurazione, l’applicazione
   chiede all’utente di registrare il fattore di autenticazione da
   utilizzare per ogni avvio successivo al primo.

4. Quando l’Utente avvia nuovamente l’applicazione, questa deve
   richiedere all’Utente il fattore di autenticazione scelto in fase di
   installazione o di prima configurazione e consentire l’accesso alle
   funzioni del RP fruibili con il Livello 1 di SPID.

5. Nel caso in cui sia necessario accedere all’applicazione con un
   livello superiore a SPID di Livello 1, occorre effettuare una nuova
   autenticazione SPID in base al livello richiesto.
