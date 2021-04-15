.. _response-1:

Response
========

Dopo avere ricevuto e validato la Token request dal client, il Token
endpoint dell’OpenID Provider (OP) restituisce una response che include
ID Token, Access Token ed un eventuale Refresh Token in formato JWT,
firmati secondo le modalità definite dall’Agenzia per l’Italia Digitale.

Access Token e ID Token devono essere formati secondo le indicazioni
dello standard “International Government Assurance Profile (iGov) for
OAuth 2.0 - Draft 03, paragrafo 3.2.1, “JWT Bearer Tokens”.

.. code-block:: json

 HTTP/1.1 200 OK
 Content-Type: application/json
 Cache-Control: no-store
 Pragma: no-cache

 {
  "access_token": "dC34Pf6kdG...",
  "token_type": "Bearer",
  "refresh_token": "wJ848BcyLP...",
  "expires_in": 1800,
  "id_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY..."
 }

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **access_token**      | L’access token, in    |                       |
|                       | formato JWT firmato,  |                       |
|                       | consente l’accesso    |                       |
|                       | allo UserInfo         |                       |
|                       | endpoint per ottenere |                       |
|                       | gli attributi.        |                       |
+-----------------------+-----------------------+-----------------------+
| **token_type**        | Tipo di *access       | Deve essere           |
|                       | token* restituito.    | valorizzato sempre    |
|                       |                       | con **Bearer**        |
+-----------------------+-----------------------+-----------------------+
| **refresh_token**     | Il *refresh token*,   |                       |
|                       | in formato JWT        |                       |
|                       | firmato, consente di  |                       |
|                       | chiamare nuovamente   |                       |
|                       | il Token Endpoint per |                       |
|                       | ottenere un nuovo     |                       |
|                       | *access token* e      |                       |
|                       | quindi recuperare una |                       |
|                       | sessione lunga        |                       |
|                       | revocabile.           |                       |
+-----------------------+-----------------------+-----------------------+
| **expires_in**        | Scadenza              | Secondo le modalità   |
|                       | dell’\ *access        | definite dall’Agenzia |
|                       | token*, in secondi.   | per l’Italia          |
|                       |                       | Digitale.             |
+-----------------------+-----------------------+-----------------------+
| **id_token**          | ID Token in formato   |                       |
|                       | JWT, firmato e        |                       |
|                       | cifrato (v. paragrafo |                       |
|                       | dedicato).            |                       |
+-----------------------+-----------------------+-----------------------+

.. forum_italia::
   :topic_id: 10927
   :scope: document
