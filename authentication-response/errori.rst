Errori
======

In caso di errore, l’OP visualizza i messaggi definiti dalle Linee Guida
UX SPID. Nei casi in cui tali linee guida prescrivono un redirect
dell’utente verso il RP, l’OP effettua il redirect verso l’URL indicata
nel parametro **redirect_uri** della richiesta (solo se valido, ovvero
presente nel client metadata), con i seguenti parametri.

**Esempio:**

+--------------------------------------------------------------------------------------------------------------------------------------------------+
| https://op.spid.agid.gov.it/resp?**error**=invalid_request&**error_description**=request%20malformata&**state**=fyZiOL9Lf2CeKuNT2JzxiLRDink0uPcd |
+--------------------------------------------------------------------------------------------------------------------------------------------------+

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **error**             | Codice dell’errore    |                       |
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
| **state**             | Valore *state*        | Il client è tenuto a  |
|                       | incluso               | verificare che        |
|                       | nell’Authentication   | corrisponda a quello  |
|                       | Request.              | inviato nella         |
|                       |                       | Authentication        |
|                       |                       | Request.              |
+-----------------------+-----------------------+-----------------------+

Di seguito i codici di errore:

+-----------------------------------+-----------------------------+
| **Scenario**                      | **Codice errore**           |
+-----------------------------------+-----------------------------+
| L’OP ha negato l’accesso a causa  | **access_denied**           |
| di credenziali non valide o non   |                             |
| adeguate al livello SPID          |                             |
| richiesto.                        |                             |
+-----------------------------------+-----------------------------+
| Il client_id indicato nella       | **invalid_client**          |
| richiesta non è riconosciuto.     |                             |
+-----------------------------------+-----------------------------+
| La richiesta non è valida a causa | **invalid_request**         |
| della mancanza o della non        |                             |
| correttezza di uno o più          |                             |
| parametri.                        |                             |
+-----------------------------------+-----------------------------+
| Sono stati richiesti degli scope  | **invalid_scope**           |
| non validi.                       |                             |
+-----------------------------------+-----------------------------+
| L’OP ha riscontrato un problema   | **server_error**            |
| interno.                          |                             |
+-----------------------------------+-----------------------------+
| L’OP ha riscontrato un problema   | **temporarily_unavailable** |
| interno temporaneo.               |                             |
+-----------------------------------+-----------------------------+

**Riferimenti:**

+-----------------------------------------------------+
| https://tools.ietf.org/html/rfc6749#section-4.1.2.1 |
+-----------------------------------------------------+
