|AGID - Agenzia per l'Italia Digitale|

Linee Guida OpenID Connect in SPID

Versione 0.1 del 23/07/2019

Sommario

`Capitolo 1 Introduzione 4 <#introduzione>`__

`1.1 Scopo 4 <#scopo>`__

`1.2 Gruppo di lavoro 5 <#gruppo-di-lavoro>`__

`Capitolo 2 Riferimenti e sigle 7 <#riferimenti-e-sigle>`__

`2.1 Riferimenti Normativi 7 <#riferimenti-normativi>`__

`2.2 Standard di riferimento 7 <#standard-di-riferimento>`__

`2.3 Termini e definizioni 8 <#termini-e-definizioni>`__

`Capitolo 3 Metadata 10 <#metadata>`__

`3.1 OpenID Provider (OP) Metadata 10 <#openid-provider-op-metadata>`__

`3.2 Client Metadata (Relying Party Metadata)
15 <#client-metadata-relying-party-metadata>`__

`Capitolo 4 Flusso 17 <#flusso>`__

`4.1 Applicazioni per dispositivi mobili
20 <#applicazioni-per-dispositivi-mobili>`__

`Capitolo 5 Authorization Endpoint (Authentication Request)
21 <#authorization-endpoint-authentication-request>`__

`5.1 Claims 24 <#claims>`__

`5.2 Generazione del code_challenge per PKCE
25 <#generazione-del-code_challenge-per-pkce>`__

`Capitolo 6 Authentication response 26 <#authentication-response>`__

`6.1 Response 26 <#response>`__

`6.2 Errori 27 <#errori>`__

`Capitolo 7 Token Endpoint (richiesta token)
29 <#token-endpoint-richiesta-token>`__

`7.1 Request 29 <#request>`__

`7.2 Response 31 <#response-1>`__

`7.3 ID Token 32 <#id-token>`__

`7.4 Errori 34 <#errori-1>`__

`Capitolo 8 UserInfo Endpoint (attributi)
36 <#userinfo-endpoint-attributi>`__

`8.1 Response 37 <#response-2>`__

`Capitolo 9 Introspection Endpoint (verifica validità token)
38 <#introspection-endpoint-verifica-validità-token>`__

`9.1 Request 38 <#request-1>`__

`9.2 Response 39 <#response-3>`__

`9.3 Errori 40 <#errori-2>`__

`Capitolo 10 Revocation Endpoint (logout)
41 <#revocation-endpoint-logout>`__

`10.1 Request 41 <#request-2>`__

`10.2 Response 42 <#response-4>`__

`Capitolo 11 Sessioni lunghe revocabili
43 <#sessioni-lunghe-revocabili>`__

`11.1 Ambiti e limiti di utilizzo 43 <#ambiti-e-limiti-di-utilizzo>`__

`11.2 Request 43 <#request-3>`__

`11.3 Refresh Token 44 <#refresh-token>`__

`11.4 Introspection 44 <#introspection>`__

`11.5 Esempio 44 <#esempio>`__

`11.6 Gestione delle sessioni 50 <#gestione-delle-sessioni>`__

`Capitolo 12 Gestione dei log 52 <#gestione-dei-log>`__

.. toctree::
  :maxdepth: 3
  :caption: Indice dei contenuti

  introduzione.rst
  riferimenti-e-sigle.rst
  metadata.rst
  flusso.rst
  authorization-endpoint-authentication-request.rst
  authentication-response.rst
  token-endpoint-richiesta-token.rst
  userinfo-endpoint-attributi.rst
  introspection-endpoint-verifica-validità-token.rst
  revocation-endpoint-logout.rst
  sessioni-lunghe-revocabili.rst
  gestione-dei-log.rst

.. |AGID - Agenzia per l'Italia Digitale| image:: ./media/image1.png
   :width: 2.76261in
   :height: 0.5849in
