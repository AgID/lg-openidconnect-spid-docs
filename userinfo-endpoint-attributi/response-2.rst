.. _response-2:

Response
========

La response dello UserInfo Endpoint deve essere firmata e cifrata
secondo le modalità definite dall’Agenzia per l’Italia Digitale. Lo
UserInfo Endpoint restituisce i claim autorizzati nella Authentication
Request.

**Esempio:**

+-------------------------------------------------------------------------+
| | {                                                                     |
| | "**iss**": "https://op.fornitore_identita.it",                        |
| | "**aud**": "https://rp.fornitore_servizio.it",                        |
| | "**ia t**": 1519032969,                                               |
| | "**nbf**": 1519032969,                                                |
| | "**exp**": 1519033149,                                                |
| | "**sub**": "OP-1234567890",                                           |
| | "**https://attributes.spid.gov.it/name**": "Mario",                   |
| | "**https://attributes.spid.gov.it/familyName**": "Rossi",             |
| | "**https://attributes.spid.gov.it/fiscalNumber**": "MROXXXXXXXXXXXXX" |
| | }                                                                     |
+-------------------------------------------------------------------------+

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **sub**               | Identificatore del    | Il RP deve verificare |
|                       | soggetto, coincidente | che il valore         |
|                       | con quello già        | coincida con quello   |
|                       | rilasciato nell’ID    | contenuto nell’ID     |
|                       | Token.                | Token.                |
+-----------------------+-----------------------+-----------------------+
| **aud**               | Identificatore del    |                       |
|                       | soggetto destinatario |                       |
|                       | della response        |                       |
+-----------------------+-----------------------+-----------------------+
| **iss**               | URI che identifica    | Il RP deve verificare |
|                       | univocamente il RP    | che il valore         |
|                       | come da Registro SPID | coincida con il       |
|                       | (client_id).          | proprio client_id.    |
+-----------------------+-----------------------+-----------------------+
| **<attributo>**       | I claim richiesti al  |                       |
|                       | momento               |                       |
|                       | dell’autenticazione   |                       |
+-----------------------+-----------------------+-----------------------+

In caso di errore di autenticazione, lo UserInfo Endpoint restituisce un
errore “HTTP 401”.
