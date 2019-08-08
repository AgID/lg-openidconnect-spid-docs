Client Metadata (Relying Party Metadata)
========================================

Il formato del metadata deriva da quanto specificato nel documento
*"OpenID Connect Discovery 1.0"*, del quale costituisce un sottoinsieme
con alcuni campi in aggiunta.

**Esempio:**

+------------------------------------------------------------------------+
|| {                                                                     |
|| "client_id": "https://rp.spid.agid.gov.it",                           |
|| "redirect_uris": [                                                    |
|| "https://rp.spid.agid.gov.it/callback1/",                             |
|| "https://rp.spid.agid.gov.it/callback2/"                              |
|| ],                                                                    |
|| "jwks_uri": "https://registry.spid.gov.it/...",                       |
|| "jwks": {"keys": [{                                                   |
|| "kty": "RSA",                                                         |
|| "alg": "RS256",                                                       |
|| "use": "sig",                                                         |
|| "kid": "e27671d73a2605ccd454413c4c94e25b3f66cdea",                    |
|| "n":                                                                  |
| "vmyoDT6ND_YJa1ItdvULuTJr2pw4MvN3Z5kmSiJBm9glVoakcDEBGF4b5c7WDh2P..."  |
| ,                                                                      |
|| "e": "ABAB"                                                           |
|| }]},                                                                  |
|| "response_types": ["code"],                                           |
|| "grant_types": ["authorization_code", "refresh_token"],               |
|| "client_name": "Agenzia per l'Italia Digitale",                       |
|| "client_name#en": "Agency for Digital Italy"                          |
|| }                                                                     |
+------------------------------------------------------------------------+

+-----------------------------------+-----------------------------------+
| **Elemento**                      | **Descrizione**                   |
+-----------------------------------+-----------------------------------+
| **client_id**                     | URI che identifica univocamente   |
|                                   | il RP come da Registro SPID.      |
+-----------------------------------+-----------------------------------+
| **redirect_uris**                 | Array di URI di redirezione       |
|                                   | utilizzati dal client (RP). Deve  |
|                                   | esserci un match esatto tra uno   |
|                                   | degli URI nell’array e quello     |
|                                   | utilizzato nell’Authentication    |
|                                   | request. Non è ammesso l’uso      |
|                                   | dello schema http (è obbligatorio |
|                                   | HTTPS); tuttavia gli URI possono  |
|                                   | seguire eventuali schemi custom   |
|                                   | (ad es. *myapp://*) al fine di    |
|                                   | supportare applicazioni mobili.   |
|                                   |                                   |
|                                   | *Come raccomandato dal Garante    |
|                                   | per la Protezione dei Dati        |
|                                   | Personali, l’URL non dovrebbe     |
|                                   | contenere informazioni utili ad   |
|                                   | individuare lo specifico servizio |
|                                   | a cui l’utente intende accedere.  |
|                                   | Si raccomanda dunque di           |
|                                   | reindirizzare verso un sistema di |
|                                   | access management che a sua volta |
|                                   | rimanderà l’utente allo specifico |
|                                   | servizio.*                        |
+-----------------------------------+-----------------------------------+
| **jwks_uri**                      | Array contenente la chiave        |
|                                   | pubblica in formato JSON Web Key  |
|                                   | (JWK) e quindi composto dai       |
|                                   | seguenti parametri:               |
|                                   |                                   |
|                                   | -  *kty:* famiglia dell’algoritmo |
|                                   |    crittografico utilizzato       |
|                                   |                                   |
|                                   | -  *alg:* algoritmo utilizzato    |
|                                   |                                   |
|                                   | -  *use:* utilizzo della chiave   |
|                                   |    pubblica per firma (sig) o     |
|                                   |    encryption (enc)               |
|                                   |                                   |
|                                   | -  *kid:* identificatore univoco  |
|                                   |    della chiave                   |
|                                   |                                   |
|                                   | -  *n:* modulus (standard pem)    |
|                                   |                                   |
|                                   | -  *e:* esponente (standard pem). |
+-----------------------------------+-----------------------------------+
| **client_name**                   | Nome del RP da visualizzare nelle |
|                                   | schermate di autenticazione e     |
|                                   | richiesta di consenso. Può essere |
|                                   | specificato in più lingue         |
|                                   | apponendo al nome dell’elemento   |
|                                   | il suffisso "#" seguito dal       |
|                                   | codice RFC5646. Un nome di        |
|                                   | default senza indicazione della   |
|                                   | lingua è sempre presente.         |
+-----------------------------------+-----------------------------------+
| **response_types**                | Array dei valori di response_type |
|                                   | previsti da OAuth 2.0 che il      |
|                                   | client userà nelle richieste di   |
|                                   | autenticazione. Deve contenere il |
|                                   | solo valore **code**.             |
+-----------------------------------+-----------------------------------+
| **grant_types**                   | Array dei valori di grant_type    |
|                                   | previsti da OAuth 2.0 che il      |
|                                   | client userà nelle richieste al   |
|                                   | Token Endpoint. Deve contenere i  |
|                                   | soli valori                       |
|                                   | **authorization_code** e          |
|                                   | **refresh_token**.                |
+-----------------------------------+-----------------------------------+

**Riferimenti**

+-----------------------------------------------------------------------+
| https://openid.net/specs/openid-connect-registration-1_0.html#ClientM |
| etadata                                                               |
+-----------------------------------------------------------------------+
