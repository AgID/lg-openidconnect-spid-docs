Gestione delle sessioni
=======================

Al fine di poter gestire le sessioni lunghe revocabili e poter
rilasciare un refresh token per il Livello 1 di SPID anche a seguito di
un’autenticazione di Livello 2 o 3 di SPID, è ammessa l’instaurazione,
per ogni livello di SPID, di una sessione di autenticazione associata ad
un determinato utente titolare di identità digitale, mantenuta dal
gestore dell’identità digitale.

Gli OP devono includere all’interno della “Pagina di gestione
dell’identità SPID”, descritta nelle Linee Guida UX SPID, un’interfaccia
per visualizzare le sessioni lunghe revocabili attive, dove l’utente
possa revocarle singolarmente o in massa.

In caso di modifica della password richiesta dall’utente, l’OP deve
prevedere la possibilità di revocare tutte le sessioni lunghe attive.

.. forum_italia::
   :topic_id: 10945
   :scope: document
