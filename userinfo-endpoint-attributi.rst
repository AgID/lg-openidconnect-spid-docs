UserInfo Endpoint (attributi) 
==============================

Lo UserInfo Endpoint è una risorsa protetta OAuth 2.0 che restituisce
attributi dell’utente autenticato. Per ottenere gli attributi richiesti
dal Relying Party, il client inoltra una richiesta allo UserInfo
endpoint utilizzando l’Access token. Il risultato è presentato in JSON e
contiene una raccolta di coppie nome e valore.

Lo UserInfo Endpoint deve supportare l'uso dei metodi HTTP GET e HTTP
POST definiti in RFC 2616 [RFC2616], accettare i token di accesso come
utilizzo di token bearer OAuth 2.0 [RFC6750] e supportare l'uso di Cross
Origin Resource Sharing (CORS) e/o altri metodi appropriati per
consentire ai client Java Script di accedere all'endpoint.

+------------------------------------------+
|| GET https://op.spid.agid.gov.it/userinfo|
|| Authorization: Bearer dC34Pf6kdG        |
+------------------------------------------+

**Riferimenti:**

+-------------------------------------------------------------------------------+
| http://openid.net/specs/openid-connect-core-1_0.html#UserInfo                 |
|                                                                               |
| https://openid.net/specs/openid-igov-openid-connect-1_0-02.html#rfc.section.4 |
+-------------------------------------------------------------------------------+

.. toctree::
  :maxdepth: 3
  :caption: Indice dei contenuti

  userinfo-endpoint-attributi/response-2.rst
