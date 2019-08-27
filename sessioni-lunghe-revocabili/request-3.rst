.. _request-3:

Request
=======

Per poter utilizzare le sessioni lunghe revocabili, l’RP include nella
Authentication Request:

-  lo scope “offline_access”, al fine di ottenere un refresh token
   utilizzabile dietro espressa consenso dell’utente;

-  il parametro “acr_values” contenente una delle seguenti opzioni:

   -  il livello SPID 1;

   -  il livello SPID 2 + il livello SPID 1.

   -  il livello SPID 3 + il livello SPID 1.

.. forum_italia::
   :topic_id: 10941
   :scope: document
