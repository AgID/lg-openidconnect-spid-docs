OpenID Provider (OP) Metadata
=============================

Il formato del metadata deriva da quanto specificato nel documento
*"OpenID Connect Discovery 1.0"*, del quale costituisce un sottoinsieme
con alcuni campi in aggiunta.

**Esempio:**

.. code-block:: json

 {
   "issuer": "https://op.fornitore_identita.it",
   "authorization_endpoint": "https://op.fornitore_identita.it/auth",
   "token_endpoint": "https://op.fornitore_identita.it/token",
   "userinfo_endpoint": "https://op.fornitore_identita.it/userinfo",
   "introspection_endpoint": "https://op.fornitore_identita.it/introspect",
   "revocation_endpoint": "https://op.fornitore_identita.it/revoke",
   "end_session_endpoint": "https://op.fornitore_identita.it/logout",
   "jwks_uri": "https://registry.spid.gov.it/...",
   "id_token_encryption_alg_values_supported": [
       "..."
   ],
   "userinfo_signing_alg_values_supported": [
       "..."
   ],
   "request_object_encryption_enc_values_supported": [
       "..."
   ],
   "token_endpoint_auth_methods_supported": ["private_key_jwt"],
   "userinfo_encryption_alg_values_supported": [
       "..."
   ],
   "id_token_encryption_enc_values_supported": [
       "..."
   ],
   "id_token_signing_alg_values_supported": [
       "..."
   ],
   "request_object_encryption_alg_values_supported": [
       "..."
   ],
   "token_endpoint_auth_signing_alg_values_supported": [
       "..."
   ],
   "request_object_signing_alg_values_supported": [
       "..."
   ],
   "userinfo_encryption_enc_values_supported": [
       "..."
   ],
   "claims_supported":[  
     "https://attributes.spid.gov.it/spidCode",
     "https://attributes.spid.gov.it/name",
     "https://attributes.spid.gov.it/familyName",
     "https://attributes.spid.gov.it/placeOfBirth",
     "https://attributes.spid.gov.it/countyOfBirth",
     "https://attributes.spid.gov.it/dateOfBirth",
     "https://attributes.spid.gov.it/gender",
     "https://attributes.spid.gov.it/companyName",
     "https://attributes.spid.gov.it/registeredOffice",
     "https://attributes.spid.gov.it/fiscalNumber",
     "https://attributes.spid.gov.it/ivaCode",
     "https://attributes.spid.gov.it/idCard",
     "https://attributes.spid.gov.it/mobilePhone",
     "https://attributes.spid.gov.it/email",
     "https://attributes.spid.gov.it/address",
     "https://attributes.spid.gov.it/expirationDate",
     "https://attributes.spid.gov.it/digitalAddress"
   ],
   "acr_values_supported":[
     "https://www.spid.gov.it/SpidL1",
     "https://www.spid.gov.it/SpidL2",
     "https://www.spid.gov.it/SpidL3
   ],
   "request_parameter_supported": true,
   "subject_types_supported":["public"],
   "op_name": "Agenzia per l'Italia Digitale",
   "op_name#en": "Agency for Digital Italy",
   "op_url": "https://www.agid.gov.it",
   "op_url#en": "https://www.agid.gov.it/en"
 }


**Esempio di risorsa jwks_uri:**

.. code-block:: json

 {
   "keys": [
     {
      "kty": "EC",
      "kid": "sig-ec256-0",
      "use": "sig",
      "crv": "P-256",
      "x": "2jM2df3IjB9VYQ0yz373-6EEot_1TBuTRaRYafMi5K0",
      "y": "h6Zlz6XReK0L-iu4ZgxlozJEXgTGUFuuDl7o8b_8JnM"
     },
     {
      "kty": "EC",
      "kid": "enc-ec256-0",
      "use": "enc",
      "crv": "P-256",
      "x": "QI31cvWP4GwnWIi-Z0IYHauQ4nPCk8Vf1BHoPazGqEc",
      "y": "DBwf8t9-abpXGtTDlZ8njjxAb33kOMrOqiGsd9oRxr0"
     }
    ]
 }

+-----------------------------------+-------------------------------------------------+
| **Elemento**                      | **Descrizione**                                 |
+-----------------------------------+-------------------------------------------------+
| **Issuer**                        | L’identificatore dell’OP (con                   |
|                                   | schema HTTPS), tipicamente l’URL                |
|                                   | base. Deve essere identico al                   |
|                                   | valore di iss negli ID Token                    |
|                                   | prodotti dall’OP. L’issuer                      |
|                                   | corrisponde al entityID che viene               |
|                                   | utilizzato in SAML e che                        |
|                                   | rappresenta la chiave univoca con               |
|                                   | cui è identificato il fornitore                 |
|                                   | di identità.                                    |
+-----------------------------------+-------------------------------------------------+
| **authorization_endpoint**        | URL dell’Authorization Endpoint,                |
|                                   | al quale il Client viene                        |
|                                   | reindirizzato per iniziare il                   |
|                                   | flusso di autenticazione.                       |
+-----------------------------------+-------------------------------------------------+
| **token_endpoint**                | URL del Token Endpoin, che il RP                |
|                                   | deve chiamare per scambiare il                  |
|                                   | codice ricevuto al termine                      |
|                                   | dell’autenticazione con un                      |
|                                   | access_token.                                   |
+-----------------------------------+-------------------------------------------------+
| **userinfo_endpoint**             | URL dello UserInfo Endpoint, che                |
|                                   | il RP può chiamare per ottenere i               |
|                                   | claim autorizzati dall’utente.                  |
+-----------------------------------+-------------------------------------------------+
| **introspection_endpoint**        | URL dell’Introspection Endpoint                 |
|                                   | (v. più avanti) che restituisce                 |
|                                   | informazioni su un token.                       |
+-----------------------------------+-------------------------------------------------+
| **revocation_endpoint**           | URL del Revocation Endpoint (v.                 |
|                                   | più avanti) che revoca un                       |
|                                   | *refresh token* o un *access                    |
|                                   | token* già rilasciato al RP                     |
|                                   | chiamante.                                      |
+-----------------------------------+-------------------------------------------------+
| **jwks_uri**                      | Url del registry dove è                         |
|                                   | localizzato il jwks che è un json               |
|                                   | array composto dai seguenti                     |
|                                   | parametri:                                      |
|                                   |                                                 |
|                                   | -  *kty:* famiglia dell’algoritmo               |
|                                   |    crittografico utilizzato                     |
|                                   |                                                 |
|                                   | -  *alg:* algoritmo utilizzato                  |
|                                   |                                                 |
|                                   | -  *use:* utilizzo della chiave                 |
|                                   |    pubblica per firma (sig) o                   |
|                                   |    encryption (enc)                             |
|                                   |                                                 |
|                                   | -  *kid:* identificatore univoco                |
|                                   |    della chiave                                 |
|                                   |                                                 |
|                                   | -  *n:* modulus (standard pem)                  |
|                                   |                                                 |
|                                   | -  *e:* esponente (standard pem)                |
+-----------------------------------+-------------------------------------------------+
| **provider_name**                 | Nome dell’OpenID Provider. Può                  |
|                                   | essere specificato in più lingue                |
|                                   | apponendo al nome dell’elemento                 |
|                                   | il suffisso "#" seguito dal                     |
|                                   | codice RFC5646. Un nome di                      |
|                                   | default senza indicazione della                 |
|                                   | lingua è sempre presente.                       |
+-----------------------------------+-------------------------------------------------+
| **provider_url**                  | URL dell’OpenID Provider. Può                   |
|                                   | essere specificato in più lingue                |
|                                   | apponendo al nome dell’elemento                 |
|                                   | il suffisso "#" seguito dal                     |
|                                   | codice RFC5646. Un valore di                    |
|                                   | default senza indicazione della                 |
|                                   | lingua è sempre presente.                       |
+-----------------------------------+-------------------------------------------------+
| **request_object_signing_alg_valu | Array contenente gli algoritmi di               |
| es_supported**                    | firma supportati per il JWS dei                 |
|                                   | Request Object. L’OP deve                       |
|                                   | supportare RS256 e può supportare               |
|                                   | anche altri algoritmi definiti in               |
|                                   | rfc7518 (3.1):                                  |
|                                   | https://tools.ietf.org/html/rfc7518#section-3.1 |
+-----------------------------------+-------------------------------------------------+
| **request_object_encryption_alg_v | Array contenente gli algoritmi di               |
| alues_supported**                 | cifratura (**alg**) supportati                  |
|                                   | per il JWS dei Request Object,                  |
|                                   | come definito in rfc7518 (4.1):                 |
|                                   | https://tools.ietf.org/html/rfc7518#section-4.1 |
+-----------------------------------+-------------------------------------------------+
| **request_object_encryption_enc_v | Array contenente gli algoritmi di               |
| alues_supported**                 | cifratura (**enc**) supportati                  |
|                                   | per il JWS dei Request Object,                  |
|                                   | come definito in rfc7518 (5.1):                 |
|                                   | https://tools.ietf.org/html/rfc7518#section-5.1 |
+-----------------------------------+-------------------------------------------------+
| **id_token_signing_alg_values_sup | Array contenente gli algoritmi di               |
| ported**                          | firma supportati per il JWS                     |
|                                   | dell’ID Token. L’OP deve                        |
|                                   | supportare RS256 e può supportare               |
|                                   | anche altri algoritmi definiti in               |
|                                   | rfc7518 (3.1):                                  |
|                                   | https://tools.ietf.org/html/rfc7518#section-3.1 |
+-----------------------------------+-------------------------------------------------+
| **id_token_encryption_alg_values_ | Array contenente gli algoritmi di               |
| supported**                       | cifratura (**alg**) supportati                  |
|                                   | per il JWS dell’ID Token, come                  |
|                                   | definito in rfc7518 (4.1):                      |
|                                   | https://tools.ietf.org/html/rfc7518#section-4.1 |
+-----------------------------------+-------------------------------------------------+
| **id_token_encryption_enc_values_ | Array contenente gli algoritmi di               |
| supported**                       | cifratura (**enc**) supportati                  |
|                                   | per il JWS dell’ID Token, come                  |
|                                   | definito in rfc7518 (5.1):                      |
|                                   | https://tools.ietf.org/html/rfc7518#section-5.1 |
+-----------------------------------+-------------------------------------------------+
| **userinfo_signing_alg_values_sup | Array contenente gli algoritmi di               |
| ported**                          | firma supportati per il JWS                     |
|                                   | dell’UserInfo Endpoint. L’OP deve               |
|                                   | supportare RS256 e può supportare               |
|                                   | anche altri algoritmi definiti in               |
|                                   | rfc7518 (3.1):                                  |
|                                   | https://tools.ietf.org/html/rfc7518#section-3.1 |
+-----------------------------------+-------------------------------------------------+
| **userinfo_encryption_alg_values_ | Array contenente gli algoritmi di               |
| supported**                       | cifratura (**alg**) supportati                  |
|                                   | per il JWE dell’UserInfo                        |
|                                   | Endpoint, come definito in                      |
|                                   | rfc7518 (4.1):                                  |
|                                   | https://tools.ietf.org/html/rfc7518#section-4.1 |
+-----------------------------------+-------------------------------------------------+
| **userinfo_encryption_enc_values_ | Array contenente gli algoritmi di               |
| supported**                       | cifratura (**enc**) supportati                  |
|                                   | per il JWE dell’UserInfo                        |
|                                   | Endpoint, come definito in                      |
|                                   | rfc7518 (5.1):                                  |
|                                   | https://tools.ietf.org/html/rfc7518#section-5.1 |
+-----------------------------------+-------------------------------------------------+
| **token_endpoint_auth_methods_sup | Array contenente i metodi di                    |
| ported**                          | autenticazione supportati dal                   |
|                                   | Token Endpoint. Deve essere                     |
|                                   | presente solo il valore                         |
|                                   | **private_key_jwt**                             |
+-----------------------------------+-------------------------------------------------+
| **acr_values_supported**          | Array contenente i livelli SPID                 |
|                                   | supportati dall’OP, rappresentati               |
|                                   | come URI. Può contenere uno o più               |
|                                   | valori tra i seguenti:                          |
|                                   |                                                 |
|                                   | - https://www.spid.gov.it/SpidL1                |
|                                   |                                                 |
|                                   | - https://www.spid.gov.it/SpidL2                |
|                                   |                                                 |
|                                   | - https://www.spid.gov.it/SpidL3                |
+-----------------------------------+-------------------------------------------------+
| **request_parameter_supported**   | Valore booleano che indica se il                |
|                                   | parametro **request** è                         |
|                                   | supportato dall’OP. Deve essere                 |
|                                   | obbligatoriamente **true**.                     |
+-----------------------------------+-------------------------------------------------+
| **subject_types_supported**       | Array contenente i tipi di                      |
|                                   | Subject Identifier supportati                   |
|                                   | dall’OP. Deve contenere il solo                 |
|                                   | valore **public**.                              |
+-----------------------------------+-------------------------------------------------+

**Riferimenti**

+-----------------------------------------------------------------------------+
| https://openid.net/specs/openid-connect-discovery-1_0.html#ProviderMetadata |
+-----------------------------------------------------------------------------+

.. forum_italia::
   :topic_id: 10915
   :scope: document
