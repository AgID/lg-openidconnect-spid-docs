Authentication response
=======================

Un’Authentication response è un messaggio di risposta di autorizzazione
OAuth 2.0 restituito dall’authorization endpoint dell'OpenID Provider
(OP) al termine del flusso di autenticazione. L’OP reindirizzerà
l’utente al redirect_uri specificato nella richiesta di autorizzazione,
aggiungendo nella post i parametri in risposta.

**Riferimenti:**

+-----------------------------------------------------------------------------+
| https://tools.ietf.org/html/rfc6749#section-4.1.2                           |
|                                                                             |
| http://openid.net/specs/openid-connect-core-1_0.html#AuthRequestValidaction |
|                                                                             |
+-----------------------------------------------------------------------------+

.. toctree::
  :maxdepth: 3
  :caption: Indice dei contenuti

  authentication-response/response.rst
  authentication-response/errori.rst
