Token Endpoint (richiesta token) 
=================================

Il Token Endpoint rilascia *access token*, *ID Token* e *refresh token*,
vi sono due scenari distinti in cui il client chiama il Token Endpoint:

1. al termine del flusso di autenticazione descritto nel paragrafo
   precedente, il Client chiama il Token Endpoint inviando
   l’Authorization code ricevuto dall’OP (code=usDwMnEzJPpG5oaV8x3j) per
   ottenere un *ID Token* e un *access token* (necessario per poi
   chiedere gli attributi/claim allo UserInfo Endpoint) ed eventualmente
   un refresh token (se è stata avviata una sessione lunga revocabile);

2. in presenza di una sessione lunga revocabile, il Client chiama il
   Token Endpoint inviando il *refresh token* in suo possesso per
   ottenere un nuovo *access token*.

**Riferimenti:**

+-----------------------------------------------------------------------+
| https://tools.ietf.org/html/rfc6749#section-3.2                       |
|                                                                       |
| http://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint    |
|                                                                       |
| http://openid.net/specs/openid-igov-oauth2-1_0-02.html#rfc.section.2. |
| 1.2                                                                   |
|                                                                       |
| http://openid.net/specs/openid-igov-openid-connect-1_0-02.html#rfc.se |
| ction.2.2                                                             |
+-----------------------------------------------------------------------+

.. toctree::
  :maxdepth: 3
  :caption: Indice dei contenuti

  token-endpoint-richiesta-token/request.rst
  token-endpoint-richiesta-token/response-1.rst
  token-endpoint-richiesta-token/id-token.rst
  token-endpoint-richiesta-token/errori-1.rst
