Authorization Endpoint (Authentication Request) 
================================================

Per avviare il processo di autenticazione, il RP manda l’utente
all’Authorization Endpoint dell’OP selezionato passando in POST o GET
una richiesta in formato JWT.

Tale richiesta DEVE essere firmata e cifrata, secondo le modalità
definite dall’Agenzia per l’Italia Digitale.

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
| **client_id**\ =https%3A%2F%2Frp.spid.agid.gov.it                     |
|                                                                       |
| | **code_challenge**\ =qWJlMe0xdbXrKxTm72EpH659bUxAxw80               |
| | **code_challenge_method**\ =S256                                    |
| | **nonce**\ =MBzGqyf9QytD28eupyWhSqMj78WNqpc2                        |
| | **prompt**\ =login                                                  |
| | **redirect_uri**\ =https%3A%2F%2Frp.spid.agid.gov.it%2Fcallback1%2F |
| | **response_type**\ =code                                            |
| | **scope**\ =openid                                                  |
|                                                                       |
| **acr_values**\ =\ `https://www.spid.gov.it/SpidL1                    |
| https://www.spid.gov.it/SpidL2                                        |
|                                                                       |
| **claims**\ ={                                                        |
|                                                                       |
| "id_token":{                                                          |
|                                                                       |
| "nbf": { essential: true},                                            |
|                                                                       |
| "jti": { essential: true }                                            |
|                                                                       |
| | },                                                                  |
| | "userinfo":{                                                        |
| | "https://attributes.spid.gov.it/name": null,                        |
| | "https://attributes.spid.gov.it/familyName": null                   |
| | },                                                                  |
| | }                                                                   |
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
| **Prompt**      | Definisce se    | **consent**:    | SI              |
|                 | l’OP deve       | l’OP chiederà   |                 |
|                 | occuparsi di    | le credenziali  |                 |
|                 | eseguire una    | di              |                 |
|                 | richiesta di    | autenticazione  |                 |
|                 | autenticazione  | all’utente (ma  |                 |
|                 | all’utente o    | solo se non è   |                 |
|                 | meno.           | già attiva una  |                 |
|                 |                 | sessione di     |                 |
|                 |                 | Single Sign-On) |                 |
|                 |                 | e               |                 |
|                 |                 | successivamente |                 |
|                 |                 | chiederà il     |                 |
|                 |                 | consenso al     |                 |
|                 |                 | trasferimento   |                 |
|                 |                 | degli attributi |                 |
|                 |                 | (valore         |                 |
|                 |                 | consigliato).   |                 |
|                 |                 |                 |                 |
|                 |                 | **consent       |                 |
|                 |                 | login:** l’OP   |                 |
|                 |                 | chiederà sempre |                 |
|                 |                 | le credenziali  |                 |
|                 |                 | di              |                 |
|                 |                 | autenticazione  |                 |
|                 |                 | all’utente e    |                 |
|                 |                 | successivamente |                 |
|                 |                 | chiederà il     |                 |
|                 |                 | consenso al     |                 |
|                 |                 | trasferimento   |                 |
|                 |                 | degli attributi |                 |
|                 |                 | (valore da      |                 |
|                 |                 | utilizzarsi     |                 |
|                 |                 | limitatamente   |                 |
|                 |                 | ai casi in cui  |                 |
|                 |                 | si vuole        |                 |
|                 |                 | forzare la      |                 |
|                 |                 | riautenticazion |                 |
|                 |                 | e)              |                 |
+-----------------+-----------------+-----------------+-----------------+
| **redirect_uri* | URL dove l’OP   | Deve essere uno | SI              |
| *               | reindirizzerà   | degli URL       |                 |
|                 | l’utente al     | indicati nel    |                 |
|                 | termine del     | client metadata |                 |
|                 | processo di     | (v. paragrafo   |                 |
|                 | autenticazione. | 3.2).           |                 |
+-----------------+-----------------+-----------------+-----------------+
| **response_type | Il tipo di      | **code**        | SI              |
| **              | credenziali che |                 |                 |
|                 | deve restituire |                 |                 |
|                 | l’OP.           |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **Scope**       | Lista degli     | **openid**      | SI              |
|                 | scope           | (obbligatorio). |                 |
|                 | richiesti.      |                 |                 |
|                 |                 | **offline_acces |                 |
|                 |                 | s**:            |                 |
|                 |                 | se specificato, |                 |
|                 |                 | l’OP rilascerà  |                 |
|                 |                 | oltre           |                 |
|                 |                 | all’\ *access   |                 |
|                 |                 | token* anche un |                 |
|                 |                 | *refresh token* |                 |
|                 |                 | necessario per  |                 |
|                 |                 | instaurare      |                 |
|                 |                 | sessioni lunghe |                 |
|                 |                 | revocabili.     |                 |
|                 |                 | L’uso di questo |                 |
|                 |                 | valore è        |                 |
|                 |                 | consentito solo |                 |
|                 |                 | se il client è  |                 |
|                 |                 | un’applicazione |                 |
|                 |                 | per dispositivi |                 |
|                 |                 | mobili che      |                 |
|                 |                 | intenda offrire |                 |
|                 |                 | all’utente una  |                 |
|                 |                 | sessione lunga  |                 |
|                 |                 | revocabile.     |                 |
+-----------------+-----------------+-----------------+-----------------+
| **acr_values**  | Valori di       | ttps://www.spi  | SI              |
|                 | riferimento     | d.gov.it/SpidL1 |                 |
|                 | della classe di |                 |                 |
|                 | contesto        | https://www.spi |                 |
|                 | dell’autenticaz | d.gov.it/SpidL2 |                 |
|                 | ione            |                 |                 |
|                 | richiesta.      | https://www.spi |                 |
|                 | Stringa         | d.gov.it/SpidL3 |                 |
|                 | separata da uno |                 |                 |
|                 | spazio, che     |                 |                 |
|                 | specifica i     |                 |                 |
|                 | valori “acr”    |                 |                 |
|                 | richiesti al    |                 |                 |
|                 | server di       |                 |                 |
|                 | autorizzazione  |                 |                 |
|                 | per             |                 |                 |
|                 | l'elaborazione  |                 |                 |
|                 | della richiesta |                 |                 |
|                 | di              |                 |                 |
|                 | autenticazione, |                 |                 |
|                 | con i valori    |                 |                 |
|                 | visualizzati in |                 |                 |
|                 | ordine di       |                 |                 |
|                 | preferenza.     |                 |                 |
+-----------------+-----------------+-----------------+-----------------+
| **Claims**      | Lista dei       | v. paragrafo    | SI              |
|                 | claims          | 5.1             |                 |
|                 | (attributi) che |                 |                 |
|                 | un RP intende   |                 |                 |
|                 | richiedere per  |                 |                 |
|                 | il servizio e   |                 |                 |
|                 | livello SPID    |                 |                 |
|                 | richiesto.      |                 |                 |
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

.. toctree::
  :maxdepth: 3
  :caption: Indice dei contenuti

  authorization-endpoint-authentication-request/claims.rst
  authorization-endpoint-authentication-request/generazione-del-code_challenge-per-pkce.rst
