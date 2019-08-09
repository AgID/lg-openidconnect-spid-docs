Response
========

Se l’autenticazione è avvenuta con successo, l’OpenID Provider (OP)
Authorization server, reindizza l’utente con i seguenti parametri:

+---------------------------------------------+
| https://op.spid.agid.gov.it/resp?           | 
|  **code**=usDwMnEzJPpG5oaV8x3j&             | 
|  **state**=fyZiOL9Lf2CeKuNT2JzxiLRDink0uPcd |
+---------------------------------------------+

+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **code**              | Codice univoco di     |                       |
|                       | autorizzazione        |                       |
|                       | (*authorization       |                       |
|                       | code*) che il client  |                       |
|                       | poi passerà al Token  |                       |
|                       | Endpoint, secondo le  |                       |
|                       | modalità definite     |                       |
|                       | dall’Agenzia per      |                       |
|                       | l’Italia Digitale.    |                       |
+-----------------------+-----------------------+-----------------------+
| **state**             | Valore state incluso  | Deve essere lo stesso |
|                       | nell’Authentication   | valore indicato dal   |
|                       | request. Il client è  | client nella          |
|                       | tenuto a verificarne  | Authorization         |
|                       | la corrispondenza.    | Request.              |
+-----------------------+-----------------------+-----------------------+
