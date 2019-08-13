.. _response-3:

Response
========

L’Introspection Endpoint risponde con un oggetto JSON definito come
segue.

**Esempio:**

.. code-block:: json

 { 
   "active": true,                        
   "scope": "foo bar",                    
   "exp": 1519033149,                     
   "sub": "OP-1234567890",                
   "client_id": "https://rp.agid.gov.it/" 
 }       


+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **active**            | Valore booleano che   |                       |
|                       | indica la validità    |                       |
|                       | del token. Se il      |                       |
|                       | token è scaduto, è    |                       |
|                       | revocato o non è mai  |                       |
|                       | stato emesso per il   |                       |
|                       | client_id chiamante,  |                       |
|                       | l’Introspection       |                       |
|                       | Endpoint deve         |                       |
|                       | restituire **false**. |                       |
+-----------------------+-----------------------+-----------------------+
| **scope**             | Lista degli scope     |                       |
|                       | richiesti al momento  |                       |
|                       | dell’Authorization    |                       |
|                       | Request.              |                       |
+-----------------------+-----------------------+-----------------------+
| **exp**               | Scadenza del token.   |                       |
+-----------------------+-----------------------+-----------------------+
| **sub**               | Identificatore del    | Il RP deve verificare |
|                       | soggetto, coincidente | che il valore         |
|                       | con quello già        | coincida con quello   |
|                       | rilasciato nell’ID    | contenuto nell’ID     |
|                       | Token.                | Token.                |
+-----------------------+-----------------------+-----------------------+
| **client_id**         | URI che identifica    | Il RP deve verificare |
|                       | univocamente il RP    | che il valore         |
|                       | come da Registro      | coincida con il       |
|                       | SPID.                 | proprio client_id.    |
+-----------------------+-----------------------+-----------------------+
