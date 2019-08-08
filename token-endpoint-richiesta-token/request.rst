Request
=======

**Esempio di richiesta con authorization code (caso 1):**

+-----------------------------------------------------------------------+
| *POST https://op.spid.agid.gov.it/token?*                             |
| **client_id=**\ https%3A%2F%2Frp.spid.agid.gov.it&                    |
| **client_assertion**\ =eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWI   |
| iOiIxMjM0NTY3ODkwIiwibmFtZSI6IlNQSUQiLCJhZG1pbiI6dHJ1ZX0.LVyRDPVJm0S9 |
| q7oiXcYVIIqGWY0wWQlqxvFGYswLF88&                                      |
| **client_assertion_type**\ =urn%3Aietf%3Aparams%3Aoauth%3Aclient-as   |
| sertion-type%3Ajwt-bearer&                                            |
| **code**\ =usDwMnEzJPpG5oaV8x3j&\                                     |
| **code_verifier**\ =9g8S40MozM3NSqjHnhi7OnsE38jklFv2&\                |
| **grant_type**\ =authorization_code                                   |
+-----------------------------------------------------------------------+

**Esempio di richiesta con refresh token (caso 2):**

+-----------------------------------------------------------------------+
| *POST https://op.spid.agid.gov.it/token?*                             |
| **client_id=**\ https%3A%2F%2Frp.spid.agid.gov.it&                    |
| **client_assertion**\ =eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWI   |
| iOiIxMjM0NTY3ODkwIiwibmFtZSI6IlNQSUQiLCJhZG1pbiI6dHJ1ZX0.LVyRDPVJm0S9 |
| q7oiXcYVIIqGWY0wWQlqxvFGYswLF88&                                      |
| **client_assertion_type**\ =urn%3Aietf%3Aparams%3Aoauth%3Aclient-as   |
| sertion-type%3Ajwt-bearer&\                                           |
| **grant_type**\ =refresh_token&                                       |
| **refresh_token**\ =8xLOxBtZp8                                        |
+-----------------------------------------------------------------------+

+-----------------+-----------------+-----------------+-----------------+
| **Parametro**   | **Descrizione** | **Valori        |**Obbligatorio** |
|                 |                 | ammessi**       |                 |
+-----------------+-----------------+-----------------+-----------------+
| **client_id**   | URI che         |                 | SI              |
|                 | identifica      |                 |                 |
|                 | univocamente il |                 |                 |
|                 | RP come da      |                 |                 |
|                 | Registro SPID.  |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **client_assert | JWT firmato con | **iat**:        | SI              |
| ion**           | la chiave       | secondo le      |                 |
|                 | privata del     | modalità        |                 |
|                 | Relying Party   | definite        |                 |
|                 | contenente i    | dall’Agenzia    |                 |
|                 | seguenti        | per l’Italia    |                 |
|                 | parametri:      | Digitale.       |                 |
|                 |                 |                 |                 |
|                 | **iss**:        | **exp**:        |                 |
|                 | Identificatore  | secondo le      |                 |
|                 | del RP          | modalità        |                 |
|                 | registrato      | definite        |                 |
|                 | presso gli OP e | dall’Agenzia    |                 |
|                 | che             | per l’Italia    |                 |
|                 | contraddistingu | Digitale.       |                 |
|                 | e               |                 |                 |
|                 | univocamente    |                 |                 |
|                 | l’entità nella  |                 |                 |
|                 | federazione nel |                 |                 |
|                 | formato Uniform |                 |                 |
|                 | Resource        |                 |                 |
|                 | Locater (URL);  |                 |                 |
|                 | corrisponde al  |                 |                 |
|                 | client_id usato |                 |                 |
|                 | nella richiesta |                 |                 |
|                 | di              |                 |                 |
|                 | autenticazione  |                 |                 |
|                 |                 |                 |                 |
|                 | **sub**: uguale |                 |                 |
|                 | al parametro    |                 |                 |
|                 | **iss**         |                 |                 |
|                 |                 |                 |                 |
|                 | **aud**: URL    |                 |                 |
|                 | del Token       |                 |                 |
|                 | Endpoint        |                 |                 |
|                 | dell’OP         |                 |                 |
|                 |                 |                 |                 |
|                 | **iat**:        |                 |                 |
|                 | data/ora in cui |                 |                 |
|                 | è stato         |                 |                 |
|                 | rilasciato il   |                 |                 |
|                 | JWT in formato  |                 |                 |
|                 | UTC             |                 |                 |
|                 |                 |                 |                 |
|                 | **exp**:        |                 |                 |
|                 | data/ora di     |                 |                 |
|                 | scadenza della  |                 |                 |
|                 | request in      |                 |                 |
|                 | formato UTC.    |                 |                 |
|                 |                 |                 |                 |
|                 | **jti**:        |                 |                 |
|                 | Identificatore  |                 |                 |
|                 | univoco per     |                 |                 |
|                 | questa          |                 |                 |
|                 | richiesta di    |                 |                 |
|                 | autenticazione, |                 |                 |
|                 | generato dal    |                 |                 |
|                 | client          |                 |                 |
|                 | casualmente con |                 |                 |
|                 | almeno 128bit   |                 |                 |
|                 | di entropia.    |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **client_assert |                 | Deve assumere   | SI              |
| ion_type**      |                 | il seguente     |                 |
|                 |                 | valore:         |                 |
|                 |                 |                 |                 |
|                 |                 | **urn:ietf:para |                 |
|                 |                 | ms:oauth:client |                 |
|                 |                 | -assertion-type |                 |
|                 |                 | :jwt-bearer**   |                 |
+-----------------+-----------------+-----------------+-----------------+
| **Code**        | Codice di       |                 | Solo se         |
|                 | autorizzazione  |                 | **grant_type**  |
|                 | restituito      |                 | è               |
|                 | nell’Authentica |                 | **authorization |
|                 | tion            |                 | _code**         |
|                 | response.       |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **code_verifier | Codice di       |                 | Solo se         |
| **              | verifica del    |                 | **grant_type**  |
|                 | code_challenge  |                 | è               |
|                 | (v paragrafo    |                 | **authorization |
|                 | 5.2)            |                 | _code**         |
+-----------------+-----------------+-----------------+-----------------+
| **grant_type**  | Tipo di         | Può assumere    | SI              |
|                 | credenziale     | uno dei         |                 |
|                 | presentata dal  | seguenti        |                 |
|                 | Client per la   | valori:         |                 |
|                 | richiesta       |                 |                 |
|                 | corrente.       | **authorization |                 |
|                 |                 | _code**         |                 |
|                 |                 |                 |                 |
|                 |                 | **refresh_token |                 |
|                 |                 | **              |                 |
+-----------------+-----------------+-----------------+-----------------+
| **refresh_token |                 |                 | Solo se         |
| **              |                 |                 | **grant_type**  |
|                 |                 |                 | è               |
|                 |                 |                 | **refresh_token |
|                 |                 |                 | **              |
+-----------------+-----------------+-----------------+-----------------+
