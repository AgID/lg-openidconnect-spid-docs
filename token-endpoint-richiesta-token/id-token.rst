ID Token
========

L’ID Token è un JSON Web Token (JWT) che contiene informazioni
sull’utente che ha eseguito l’autenticazione. I Client devono eseguire
la validazione dell’ID Token.

**Esempio di ID Token:**

+---------------------------------------------------+
| | {                                               |
| | "**iss**": "https://rp.spid.agid.gov.it/",      |
| | "**sub**": "OP-1234567890",                     |
| | "**aud**": "https://op.spid.agid.gov.it/auth",  |
| | "**acr**": "https://www.spid.gov.it/SpidL2",    |
| | "**at_hash**": "qiyh4XPJGsOZ2MEAyLkfWqeQ",      |
| | "**iat**": 1519032969,                          |
| | "**nbf**": 1519032969,                          |
| | "**exp**": 1519033149,                          |
| | "**jti**": "nw4J0zMwRk4kRbQ53G7z",              |
| | "**nonce**": "MBzGqyf9QytD28eupyWhSqMj78WNqpc2" |
| | }                                               |
+---------------------------------------------------+

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Validazione**       |
+-----------------------+-----------------------+-----------------------+
| **Iss**               | Identificatore        | Il client è tenuto a  |
|                       | dell’OP che lo        | verificare che questo |
|                       | contraddistingue      | valore corrisponda    |
|                       | univocamente nella    | all’OP chiamato.      |
|                       | federazione nel       |                       |
|                       | formato Uniform       |                       |
|                       | Resource Locator      |                       |
|                       | (URL).                |                       |
+-----------------------+-----------------------+-----------------------+
| **Sub**               | Per il valore di      |                       |
|                       | questo parametro fare |                       |
|                       | riferimento allo      |                       |
|                       | standard “OpenID      |                       |
|                       | Connect Core 1.0”,    |                       |
|                       | paragrafo 8.1.        |                       |
|                       | “Pairwise Identifier  |                       |
|                       | Algorithm”.           |                       |
+-----------------------+-----------------------+-----------------------+
| **Aud**               | Contiene il client    | Il client è tenuto a  |
|                       | ID.                   | verificare che questo |
|                       |                       | valore corrisponda al |
|                       |                       | proprio client ID.    |
+-----------------------+-----------------------+-----------------------+
| **Acr**               | Livello di            |                       |
|                       | autenticazione        |                       |
|                       | effettivo. Può essere |                       |
|                       | uguale o superiore a  |                       |
|                       | quello richiesto dal  |                       |
|                       | client nella          |                       |
|                       | Authentication        |                       |
|                       | Request.              |                       |
+-----------------------+-----------------------+-----------------------+
| **at_hash**           | Hash dell’Access      | Il client è tenuto a  |
|                       | Token; il suo valore  | verificare che questo |
|                       | è                     | valore corrisponda    |
|                       | la codifica base64url | all’\ *access token*  |
|                       | della prima metà      | restituito insieme    |
|                       | dell’hash del valore  | all’ID Token.         |
|                       | access_token, usando  |                       |
|                       | l’algoritmo di        |                       |
|                       | hashing indicato in   |                       |
|                       | **alg** nell’header   |                       |
|                       | dell’ID Token.        |                       |
+-----------------------+-----------------------+-----------------------+
| **Iat**               | Data/ora di emissione |                       |
|                       | del token in formato  |                       |
|                       | UTC.                  |                       |
+-----------------------+-----------------------+-----------------------+
| **Nbf**               | Data/ora di inizio    ||{                     |
|                       | validità del token in ||userinfo: {...}       |
|                       | formato UTC. Deve     ||id_token: {           |
|                       | corrispondere con il  ||acr: {...},           |
|                       | valore di **iat**.    ||nbf: { essential:     |
|                       |                       | true},                |
|                       |                       ||jti: { essential:     |
|                       |                       | true }                |
|                       |                       ||}                     |
|                       |                       ||}                     |
+-----------------------+-----------------------+-----------------------+
| **Exp**               | Data/ora di scadenza  |                       |
|                       | del token in formato  |                       |
|                       | UTC, secondo le       |                       |
|                       | modalità definite     |                       |
|                       | dall’Agenzia per      |                       |
|                       | l’Italia Digitale.    |                       |
+-----------------------+-----------------------+-----------------------+
| **Jti**               | Identificatore unico  |                       |
|                       | dell’ID Token che il  |                       |
|                       | client più utilizzare |                       |
|                       | per prevenirne il     |                       |
|                       | riuso, rifiutando     |                       |
|                       | l’ID Token se già     |                       |
|                       | processato. Deve      |                       |
|                       | essere di difficile   |                       |
|                       | individuazione da     |                       |
|                       | parte di un           |                       |
|                       | attaccante e composto |                       |
|                       | da una stringa        |                       |
|                       | casuale.              |                       |
+-----------------------+-----------------------+-----------------------+
| **Nonce**             | Stringa casuale       | Il client è tenuto a  |
|                       | generata dal Client   | verificare che        |
|                       | per ciascuna sessione | coincida con quella   |
|                       | utente ed inviata     | inviata               |
|                       | nell’Authentication   | nell’Authentication   |
|                       | Request (parametro    | Request.              |
|                       | nonce), finalizzata a |                       |
|                       | mitigare attacchi     |                       |
|                       | replay.               |                       |
+-----------------------+-----------------------+-----------------------+

**Riferimenti:**

+-----------------------------------------------------------------------+
| http://openid.net/specs/openid-connect-core-1_0.html#IDToken          |
|                                                                       |
| https://openid.net/specs/openid-igov-openid-connect-1_0-02.html#rfc.s |
| ection.3.1                                                            |
+-----------------------------------------------------------------------+
