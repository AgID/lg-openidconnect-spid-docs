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

+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|| GET https://op.spid.agid.gov.it/userinfo                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|| Authorization: Bearer eyJhbGciOiJSUzI1NiJ9.eyJleHAiOjE0MTg3MDI0MTIsImF1ZCI6WyJjMWJjODRlNC00N2VlLTRiNjQtYmI1Mi01Y2RhNmM4MWY3ODgiXSwiaXNzIjoiaHR0cHM6XC9cL2lkcC1wLmV4YW1wbGUuY29tXC8iLCJqdGkiOiJkM2Y3YjQ4Zi1iYzgxLTQwZWMtYTE0MC05NzRhZjc0YzRkZTMiLCJpYXQiOjE0MTg2OTg4MTJ9i.HMz_tzZ90_b0QZS-AXtQtvclZ7M4uDAs1WxCFxpgBfBanolW37X8h1ECrUJexbXMD6rrj_uuWEqPD738oWRo0rOnoKJAgbF1GhXPAYnN5pZRygWSD1a6RcmN85SxUig0H0e7drmdmRkPQgbl2wMhu-6h2Oqw-ize4dKmykN9UX_2drXrooSxpRZqFVYX8PkCvCCBuFy2O-HPRov_SwtJMk5qjUWMyn2I4Nu2s-R20aCA-7T5dunr0iWCkLQnVnaXMfA22RlRiU87nl21zappYb1_EHF9ePyq3Q353cDUY7vje8m2kKXYTgc_bUAYuW-W3SMSw5UlKaHtSZ6PQICoA |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. forum_italia::
   :topic_id: 10930
   :scope: document
