Revocation Endpoint (logout) 
=============================

Il Revocation Endpoint consente al RP di chiedere la revoca di un
*access token* o di un *refresh token* in suo possesso.

Quando l’utente esegue il logout, o quando la sua sessione presso il RP
scade (in base alle policy decise da quest’ultimo), il RP deve chiamare
questo endpoint per revocare l’\ *access token* e l’eventuale *refresh
token* in suo possesso.

L’OP dovrà revocare il token specificato nella richiesta e dovrà
terminare la sessione di Single Sign-On se ancora attiva. Eventuali
altri token attivi per l’utente dovranno invece essere mantenuti validi.

**Riferimenti:**

+-------------------------------------+
| https://tools.ietf.org/html/rfc7009 |
+-------------------------------------+

.. toctree::
  :maxdepth: 3
  :caption: Indice dei contenuti

  revocation-endpoint-logout/request-2.rst
  revocation-endpoint-logout/response-4.rst

.. forum_italia::
   :topic_id: 10936
   :scope: document
