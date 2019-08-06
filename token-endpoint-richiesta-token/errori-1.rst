.. _errori-1:

Errori
======

In caso di errore, l’OP restituisce un codice HTTP 401 con un JSON nel
body avente gli elementi di seguito indicati.

**Esempio:**

+---------------------------------------------------+
| {                                                 |
|                                                   |
| "error": "invalid_client",                        |
|                                                   |
| "error_description: "client_id non riconosciuto." |
|                                                   |
| }                                                 |
+---------------------------------------------------+

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **Error**             | Codice dell’errore    |                       |
|                       | (v. tabella sotto)    |                       |
+-----------------------+-----------------------+-----------------------+
| **error_description** | Descrizione più       |                       |
|                       | dettagliata           |                       |
|                       | dell’errore,          |                       |
|                       | finalizzata ad        |                       |
|                       | aiutare lo            |                       |
|                       | sviluppatore per      |                       |
|                       | eventuale debugging.  |                       |
|                       | Questo messaggio non  |                       |
|                       | è destinato ad essere |                       |
|                       | visualizzato          |                       |
|                       | all’utente (a tal     |                       |
|                       | fine si faccia        |                       |
|                       | riferimento alle      |                       |
|                       | Linee Guida UX SPID). |                       |
+-----------------------+-----------------------+-----------------------+

Di seguito i codici di errore:

+-----------------------------------+-----------------------------------+
| **Scenario**                      | **Codice errore**                 |
+-----------------------------------+-----------------------------------+
| Il client_id indicato nella       | **invalid_client**                |
| richiesta non è riconosciuto.     |                                   |
+-----------------------------------+-----------------------------------+
| Il parametro **grant_type**       | **unsupported_grant_type**        |
| contiene un valore non corretto.  |                                   |
+-----------------------------------+-----------------------------------+
| I parametri **grant_type**,       | **invalid_grant**                 |
| **code**, **code_verifier**,      |                                   |
| **access_token** non sono validi. |                                   |
+-----------------------------------+-----------------------------------+
| La richiesta non è valida a causa | **invalid_request**               |
| della mancanza o della non        |                                   |
| correttezza di uno o più          |                                   |
| parametri.                        |                                   |
+-----------------------------------+-----------------------------------+
| L’OP ha riscontrato un problema   | **server_error**                  |
| interno.                          |                                   |
+-----------------------------------+-----------------------------------+
| L’OP ha riscontrato un problema   | **temporarily_unavailable**       |
| interno temporaneo.               |                                   |
+-----------------------------------+-----------------------------------+

**Riferimenti:**

+-------------------------------------------------------------------------+
| https://tools.ietf.org/html/rfc6749#section-5.2                         |
|                                                                         |
| http://openid.net/specs/openid-connect-core-1_0.html#TokenErrorResponse |
+-------------------------------------------------------------------------+
