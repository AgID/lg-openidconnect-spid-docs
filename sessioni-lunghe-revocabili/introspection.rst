Introspection
=============

Ad ogni successivo avvio della propria applicazione, il RP può inviare
una richiesta all’Introspection Endpoint per verificare che l’\ *access
token* in suo possesso sia ancora valido.

In caso negativo, deve inviare una richiesta al Token Endpoint con il
*refresh token* in suo possesso, per ottenere un nuovo *access token*.

Nel caso in cui il Token Endpoint rifiuti la concessione di un nuovo
*access token*, l’utente dovrà effettuare un nuovo login SPID.

.. forum_italia::
   :topic_id: 10943
   :scope: document
