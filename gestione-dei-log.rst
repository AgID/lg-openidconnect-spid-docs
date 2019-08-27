Gestione dei log
================

OpenID Provider e Relying party devono conservare i log di ogni
autenticazione e devono essere mantenuti per un tempo pari a 24 mesi.

In particolare devono essere conservate le evidenze di:

-  rilascio di ID e access token a fronte di autenticazione;

-  rilascio di refresh token a fronte di autenticazione;

-  rilascio di ID e access token a fronte di utilizzo del refresh token.

Per ogni rilascio devono essere conservati JWT costituenti richiesta e
risposta, occorre, inoltre, tracciare le chiamate e le relative risposte
effettuate verso ogni endpoint.

Le tracciature devono essere mantenute nel rispetto del codice della
privacy sotto la responsabilità dell’OpenID Provider o del Relying Party
e l’accesso ai dati di tracciatura deve essere riservato a personale
incaricato.

Al fine di garantire la confidenzialità potrebbero essere adottati
meccanismi di cifratura dei dati o impiegati sistemi di basi di dati
(DBMS) che realizzano la persistenza cifrata delle informazioni.

Per il mantenimento devono essere messi in atto meccanismi che
garantiscono l’integrità e il non ripudio.

.. forum_italia::
   :topic_id: 10946
   :scope: document
