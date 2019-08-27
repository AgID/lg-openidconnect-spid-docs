Termini e definizioni
=====================

Essendo le funzionalità simili, ritroviamo gli stessi concetti di SAML
2.0 anche in OpenID Connect:

+-------------------------+----------------------------+
| **SAML 2.0**            | **OpenID Connect**         |
+-------------------------+----------------------------+
| Assertion               | *ID Token*                 |
+-------------------------+----------------------------+
| Attribute query         | *UserInfo Endpoint*        |
+-------------------------+----------------------------+
| Authentication request  | *Authentication request*   |
+-------------------------+----------------------------+
| ForceAuthn              | *prompt=login*             |
+-------------------------+----------------------------+
| Identity Provider (IdP) | *OpenID Provider (OP)*     |
+-------------------------+----------------------------+
| IdP metadata            | *OpenID Provider metadata* |
+-------------------------+----------------------------+
| Issuer                  | *Issuer*                   |
+-------------------------+----------------------------+
| Logout                  | *Revoke*                   |
+-------------------------+----------------------------+
| NameID policy           | *Subject identifier type*  |
+-------------------------+----------------------------+
| Passive Authentication  | *prompt=none*              |
+-------------------------+----------------------------+
| Service Provider (SP)   | *Relying Party (RP)*       |
+-------------------------+----------------------------+
| SP metadata             | *Client metadata*          |
+-------------------------+----------------------------+
| Subject                 | *Subject Identifier*       |
+-------------------------+----------------------------+
| Attributes              | *Claims*                   |
+-------------------------+----------------------------+

Ai fini delle presenti Linee Guida, per *OpenID Provider (OP)* e
*Relying Party (RP)* si intendono rispettivamente i Gestori
dell'identità digitale (Identity Provider - IdP) e i Fornitori di
servizi (Service Provider - SP) di cui al DPCM 24 ottobre 2014,
“Definizione delle caratteristiche del sistema pubblico per la gestione
dell'identità digitale di cittadini e imprese (SPID), nonché dei tempi e
delle modalità di adozione del sistema SPID da parte delle pubbliche
amministrazioni e delle imprese.”

.. forum_italia::
   :topic_id: 10913
   :scope: document
