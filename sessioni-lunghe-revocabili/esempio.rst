Esempio
=======

Un RP fornisce servizi per i quali è necessaria un’autenticazione di liv
1 o di livello 2.

Il RP, per consentire l’accesso, effettua una richiesta di
autenticazione, all’OP con acr_values=\ https://www.spid.gov.it/SpidL2
https://www.spid.gov.it/SpidL1

L’“authorization server” autentica l’utente, sulla base del Livello SPID
richiesto dal RP (Livello 1 o Livello 2 o Livello 3), c.d.
“autenticazione originaria”, e rilascia un unico “access_token” sia per
il Livello SPID 1 sia per il Livello SPID richiesto dal SP, con una
scadenza di 15 minuti, e rilascia un “refresh_token” per il solo livello
SPID 1 con scadenza 30 giorni.

L’OP consente l’accesso sia al livello "SPID1" sia al livello "SPID2"
per 15 mins mediante l’“access_token”.

Quando l’“access_token” scade, l’OP non consente l’accesso con tale
l'access token e il RP deve ottenere un nuovo "access_token" tramite
nuova autenticazione oppure tramite una "richiesta di refresh".

Il RP effettua una “richiesta di refresh” con il refresh_token.

Il “token endpoint” verifica la validità del refresh_token, e se nella
richiesta di autenticazione originaria era presente nell’“acr_values” il
livello “SPID1”, rilascia un nuovo ID Token valido esclusivamente per il
livello "SPID1" con scadenza a 30 giorni dall’autenticazione originaria.

**Esempio (chiamata HTTP):**

+-----------------------------------------------------------------------+
| https://op.spid.agid.gov.it/auth?\ **request**\ =eyJhbGciOiJSUzI1NiIs |
| ImtpZCI6ImsyYmRjIn0.ew0KICJpc3MiOiAiczZCaGRSa3F0MyIsDQogImF1ZCI6ICJod |
| HRwczovL3NlcnZlci5leGFtcGxlLmNvbSIsDQogInJlc3BvbnNlX3R5cGUiOiAiY29kZS |
| BpZF90b2tlbiIsDQogImNsaWVudF9pZCI6ICJzNkJoZFJrcXQzIiwNCiAicmVkaXJlY3R |
| fdXJpIjogImh0dHBzOi8vY2xpZW50LmV4YW1wbGUub3JnL2NiIiwNCiAic2NvcGUiOiAi |
| b3BlbmlkIiwNCiAic3RhdGUiOiAiYWYwaWZqc2xka2oiLA0KICJub25jZSI6ICJuLTBTN |
| l9XekEyTWoiLA0KICJtYXhfYWdlIjogODY0MDAsDQogImNsYWltcyI6IA0KICB7DQogIC |
| AidXNlcmluZm8iOiANCiAgICB7DQogICAgICJnaXZlbl9uYW1lIjogeyJlc3NlbnRpYWw |
| iOiB0cnVlfSwNCiAgICAgIm5p                                             |
+-----------------------------------------------------------------------+

**Esempio (contenuto del JWT):**

+-----------------------------------------------------------------------+
| {                                                                     |
|                                                                       |
| **client_id**\ =https%3A%2F%2Frp.spid.agid.gov.it,                    |
|                                                                       |
| | **code_challenge**\ =qWJlMe0xdbXrKxTm72EpH659bUxAxw80,              |
| | **code_challenge_method**\ =S256,                                   |
| | **nonce**\ =MBzGqyf9QytD28eupyWhSqMj78WNqpc2                        |
| | **prompt**\ =login,                                                 |
| | **redirect_uri**\ =https%3A%2F%2Frp.spid.agid.gov.it%2Fcallback1%2F |
| ,                                                                     |
| | **response_type**\ =code,                                           |
| | **scope**\ =openid offline_access,                                  |
|                                                                       |
| **acr_values=**\ https://www.spid.gov.it/SpidL2                       |
| https://www.spid.gov.it/SpidL1,                                       |
|                                                                       |
| | **claims**\ ={                                                      |
| | "userinfo":{                                                        |
| | "https://attributes.spid.gov.it/name": null,                        |
| | "https://attributes.spid.gov.it/familyName": null                   |
| | },                                                                  |
| | }&                                                                  |
| | **state**\ =fyZiOL9Lf2CeKuNT2JzxiLRDink0uPcd                        |
|                                                                       |
| }                                                                     |
+-----------------------------------------------------------------------+

+-----------------+-----------------+-----------------+-----------------+
| **Parametro**   | **Descrizione** | **Valori        | **Obbligatorio* |
|                 |                 | ammessi**       | *               |
+-----------------+-----------------+-----------------+-----------------+
| **client_id**   | URI che         | Deve            | SI              |
|                 | identifica      | corrispondere   |                 |
|                 | univocamente il | ad un valore    |                 |
|                 | RP come da      | nel Registro    |                 |
|                 | Registro SPID.  | SPID.           |                 |
+-----------------+-----------------+-----------------+-----------------+
| **code_challeng | Un challenge    | V. paragrafo    | SI              |
| e**             | per PKCE da     | 6.1             |                 |
|                 | riportare anche | "Generazione    |                 |
|                 | nella           | del             |                 |
|                 | successiva      | code_challenge  |                 |
|                 | richiesta al    | per PKCE"       |                 |
|                 | Token endpoint. |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **code_challeng | Metodo di       | È obbligatorio  | SI              |
| e_method**      | costruzione del | specificare il  |                 |
|                 | challenge PKCE. | valore **S256** |                 |
+-----------------+-----------------+-----------------+-----------------+
| **Nonce**       | Valore che      | Stringa di      | SI              |
|                 | serve ad        | almeno 32       |                 |
|                 | evitare         | caratteri       |                 |
|                 | attacchi Reply, | alfanumerici.   |                 |
|                 | generato        |                 |                 |
|                 | casualmente e   |                 |                 |
|                 | non prevedibile |                 |                 |
|                 | da terzi.       |                 |                 |
|                 | Questo valore   |                 |                 |
|                 | sarà restituito |                 |                 |
|                 | nell’ID Token   |                 |                 |
|                 | fornito dal     |                 |                 |
|                 | Token Endpoint, |                 |                 |
|                 | in modo da      |                 |                 |
|                 | consentire al   |                 |                 |
|                 | client di       |                 |                 |
|                 | verificare che  |                 |                 |
|                 | sia uguale a    |                 |                 |
|                 | quello inviato  |                 |                 |
|                 | nella richiesta |                 |                 |
|                 | di              |                 |                 |
|                 | autenticazione. |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **Prompt**      | Definisce se    | -  **consent**: | SI              |
|                 | l’OP deve       |    l’OP         |                 |
|                 | occuparsi di    |    chiederà le  |                 |
|                 | eseguire una    |    credenziali  |                 |
|                 | richiesta di    |    di           |                 |
|                 | autenticazione  |    autenticazio |                 |
|                 | all’utente o    | ne              |                 |
|                 | meno.           |    all’utente   |                 |
|                 |                 |    (ma solo se  |                 |
|                 |                 |    non è già    |                 |
|                 |                 |    attiva una   |                 |
|                 |                 |    sessione di  |                 |
|                 |                 |    Single       |                 |
|                 |                 |    Sign-On) e   |                 |
|                 |                 |    successivame |                 |
|                 |                 | nte             |                 |
|                 |                 |    chiederà il  |                 |
|                 |                 |    consenso al  |                 |
|                 |                 |    trasferiment |                 |
|                 |                 | o               |                 |
|                 |                 |    degli        |                 |
|                 |                 |    attributi    |                 |
|                 |                 |    (valore      |                 |
|                 |                 |    consigliato) |                 |
|                 |                 |                 |                 |
|                 |                 | -  **consent    |                 |
|                 |                 |    login:**     |                 |
|                 |                 |    l’OP         |                 |
|                 |                 |    chiederà     |                 |
|                 |                 |    sempre le    |                 |
|                 |                 |    credenziali  |                 |
|                 |                 |    di           |                 |
|                 |                 |    autenticazio |                 |
|                 |                 | ne              |                 |
|                 |                 |    all’utente e |                 |
|                 |                 |    successivame |                 |
|                 |                 | nte             |                 |
|                 |                 |    chiederà il  |                 |
|                 |                 |    consenso al  |                 |
|                 |                 |    trasferiment |                 |
|                 |                 | o               |                 |
|                 |                 |    degli        |                 |
|                 |                 |    attributi    |                 |
|                 |                 |    (valore da   |                 |
|                 |                 |    utilizzarsi  |                 |
|                 |                 |    limitatament |                 |
|                 |                 | e               |                 |
|                 |                 |    ai casi in   |                 |
|                 |                 |    cui si vuole |                 |
|                 |                 |    forzare la   |                 |
|                 |                 |    riautenticaz |                 |
|                 |                 | ione)           |                 |
+-----------------+-----------------+-----------------+-----------------+
| **redirect_uri* | URL dove l’OP   | Deve essere uno | SI              |
| *               | reindirizzerà   | degli URL       |                 |
|                 | l’utente al     | indicati nel    |                 |
|                 | termine del     | client metadata |                 |
|                 | processo di     | (v. paragrafo   |                 |
|                 | autenticazione. | 3.2).           |                 |
+-----------------+-----------------+-----------------+-----------------+
| **response_type | Il tipo di      | -  **code**     | SI              |
| **              | credenziali che |                 |                 |
|                 | deve restituire |                 |                 |
|                 | l’OP.           |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **Scope**       | Lista degli     | -  **openid**   | SI              |
|                 | scope           |    (obbligatori |                 |
|                 | richiesti.      | o)              |                 |
|                 |                 |                 |                 |
|                 |                 | -  **offline_ac |                 |
|                 |                 | cess**:         |                 |
|                 |                 |    se           |                 |
|                 |                 |    specificato, |                 |
|                 |                 |    l’OP         |                 |
|                 |                 |    rilascerà    |                 |
|                 |                 |    oltre        |                 |
|                 |                 |    all’\ *acces |                 |
|                 |                 | s               |                 |
|                 |                 |    token* anche |                 |
|                 |                 |    un *refresh  |                 |
|                 |                 |    token*       |                 |
|                 |                 |    necessario   |                 |
|                 |                 |    per          |                 |
|                 |                 |    instaurare   |                 |
|                 |                 |    sessioni     |                 |
|                 |                 |    lunghe       |                 |
|                 |                 |    revocabili.  |                 |
|                 |                 |    L’uso di     |                 |
|                 |                 |    questo       |                 |
|                 |                 |    valore è     |                 |
|                 |                 |    consentito   |                 |
|                 |                 |    solo se il   |                 |
|                 |                 |    client è     |                 |
|                 |                 |    un’applicazi |                 |
|                 |                 | one             |                 |
|                 |                 |    per          |                 |
|                 |                 |    dispositivi  |                 |
|                 |                 |    mobili che   |                 |
|                 |                 |    intenda      |                 |
|                 |                 |    offrire      |                 |
|                 |                 |    all’utente   |                 |
|                 |                 |    una sessione |                 |
|                 |                 |    lunga        |                 |
|                 |                 |    revocabile.  |                 |
+-----------------+-----------------+-----------------+-----------------+
| **Claims**      | Lista dei       | v. paragrafo    | SI              |
|                 | claims          | 5.1             |                 |
|                 | (attributi) che |                 |                 |
|                 | un RP intende   |                 |                 |
|                 | richiedere per  |                 |                 |
|                 | il servizio.    |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **acr_values**  | Livello minimo  | Se sono         | SI              |
|                 | SPID richiesto. | richiesti più   |                 |
|                 |                 | livelli,        |                 |
|                 |                 | occorre         |                 |
|                 |                 | indicarli in    |                 |
|                 |                 | ordine di       |                 |
|                 |                 | preferenza      |                 |
|                 |                 | separati da uno |                 |
|                 |                 | spazio.         |                 |
+-----------------+-----------------+-----------------+-----------------+
| **State**       | Valore univoco  | Stringa di      | SI              |
|                 | utilizzato per  | almeno 32       |                 |
|                 | mantenere lo    | caratteri       |                 |
|                 | stato tra la    | alfanumerici.   |                 |
|                 | request e il    |                 |                 |
|                 | callback.       |                 |                 |
|                 | Questo valore   |                 |                 |
|                 | verrà           |                 |                 |
|                 | restituito al   |                 |                 |
|                 | client nella    |                 |                 |
|                 | risposta al     |                 |                 |
|                 | termine         |                 |                 |
|                 | dell’autenticaz |                 |                 |
|                 | ione.           |                 |                 |
|                 |                 |                 |                 |
|                 | Il valore deve  |                 |                 |
|                 | essere          |                 |                 |
|                 | significativo   |                 |                 |
|                 | esclusivamente  |                 |                 |
|                 | per il RP e non |                 |                 |
|                 | deve essere     |                 |                 |
|                 | intellegibile   |                 |                 |
|                 | ad altri.       |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **response_mode | http://openid.n | form_post       | SI              |
| **              | et/specs/oauth- |                 |                 |
|                 | v2-form-post-re |                 |                 |
|                 | sponse-mode-1_0 |                 |                 |
|                 | .html#FormPostR |                 |                 |
|                 | esponseMode     |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **ui_locales**  | Lingue          | Lista di codici | NO              |
|                 | preferibili per | RFC5646         |                 |
|                 | visualizzare le | separati da     |                 |
|                 | pagine dell’OP. | spazi.          |                 |
|                 | L’OP può        |                 |                 |
|                 | ignorare questo |                 |                 |
|                 | parametro se    |                 |                 |
|                 | non dispone di  |                 |                 |
|                 | nessuna delle   |                 |                 |
|                 | lingue          |                 |                 |
|                 | indicate.       |                 |                 |
+-----------------+-----------------+-----------------+-----------------+

**Riferimenti:**

+-----------------------------------------------------------------------+
| http://openid.net/specs/openid-connect-core-1_0.html#AuthRequest      |
|                                                                       |
| http://openid.net/specs/openid-igov-oauth2-1_0-02.html#rfc.section.2. |
| 1.1                                                                   |
|                                                                       |
| http://openid.net/specs/openid-igov-openid-connect-1_0-02.html#rfc.se |
| ction.2.1                                                             |
|                                                                       |
| http://openid.net/specs/openid-igov-openid-connect-1_0-02.html#rfc.se |
| ction.2.4                                                             |
|                                                                       |
| http://openid.net/specs/openid-connect-core-1_0.html#JWTRequests      |
+-----------------------------------------------------------------------+

**Esempio Refresh (chiamata HTTP):**

+---------------------------------------------------+
| POST /token HTTP/1.1                              |
|                                                   |
| Host: server.example.com                          |
|                                                   |
| Content-Type: application/x-www-form-urlencoded   |
|                                                   |
| **client_id**\ =https%3A%2F%2Frp.spid.agid.gov.it |
|                                                   |
| &\ **grant_type**\ =refresh_token                 |
|                                                   |
| &\ **refresh_token**\ =8xLOxBtZp8                 |
|                                                   |
| &\ **scope**\ =opened                             |
+---------------------------------------------------+

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **client_id**         | URI che identifica    | Deve corrispondere    |
|                       | univocamente il RP    | alm valore del        |
|                       | come da Registro      | client_id della       |
|                       | SPID.                 | authentication        |
|                       |                       | request.              |
+-----------------------+-----------------------+-----------------------+
| **grant_type**        | Tipo di credenziale   | Deve assumere il      |
|                       | presentata dal Client | valore:               |
|                       | per la richiesta      | **refresh_token**     |
|                       | corrente.             |                       |
+-----------------------+-----------------------+-----------------------+
| **refresh_token**     |                       |                       |
+-----------------------+-----------------------+-----------------------+
| **Scope**             |                       | openid                |
+-----------------------+-----------------------+-----------------------+

Nel caso in cui il Token Endpoint rifiuti la concessione di un nuovo *ID
token* e *access token*, l’utente dovrà effettuare un nuovo login SPID.

Nel caso in cui sia necessario accedere all’applicazione con un livello
superiore a SPID di Livello 1, occorre effettuare una nuova
autenticazione SPID in base al livello richiesto.

Se la Refresh Request è valida, l’OpenID Connect Provider restituisce un
ID Token con i seguenti parametri:

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **Iss**               | Identificatore        | Deve essere lo stesso |
|                       | dell’OP che lo        | indicato nell'ID      |
|                       | contraddistingue      | Token emesso          |
|                       | univocamente nella    | nell'autenticazione   |
|                       | federazione nel       | originaria.           |
|                       | formato Uniform       |                       |
|                       | Resource Locator      |                       |
|                       | (URL).                |                       |
+-----------------------+-----------------------+-----------------------+
| **Sub**               | Per il valore di      | Deve essere lo stesso |
|                       | questo parametro fare | indicato nell'ID      |
|                       | riferimento allo      | Token emesso          |
|                       | standard “OpenID      | nell'autenticazione   |
|                       | Connect Core 1.0”,    | originaria.           |
|                       | paragrafo 8.1.        |                       |
|                       | “Pairwise Identifier  |                       |
|                       | Algorithm”.           |                       |
+-----------------------+-----------------------+-----------------------+
| **Aud**               | Contiene il client    | Deve essere lo stesso |
|                       | ID.                   | indicato nell'ID      |
|                       |                       | Token emesso          |
|                       |                       | nell'autenticazione   |
|                       |                       | originaria.           |
+-----------------------+-----------------------+-----------------------+
| **Acr**               | Livello di            | https://www.spid.gov. |
|                       | autenticazione        | it/SpidL1             |
|                       | ammesso a seguito di  |                       |
|                       | richiesta di refresh  |                       |
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
| **Nbf**               | Data/ora di inizio    |                       |
|                       | validità del token in |                       |
|                       | formato UTC. Deve     |                       |
|                       | corrispondere con il  |                       |
|                       | valore di **iat**.    |                       |
+-----------------------+-----------------------+-----------------------+
| **Exp**               | Data/ora di scadenza  |                       |
|                       | del token in formato  |                       |
|                       | UTC                   |                       |
+-----------------------+-----------------------+-----------------------+
| **Jti**               | Identificatore unico  |                       |
|                       | dell’ID Token che il  |                       |
|                       | client può utilizzare |                       |
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

Il refresh token ottenuto con la richiesta di autenticazione ha una
validità massima di 30 giorni, entro i quali potrà essere utilizzato un
numero illimitato di volte. Allo scadere dei 30 giorni non potrà più
essere utilizzato e sarà necessario rieseguire l’autenticazione
completa.
