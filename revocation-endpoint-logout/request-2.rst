.. _request-2:

Request
=======

La richiesta al Revocation Endpoint consiste nell’invio del token che si
vuole revocare unitamente ad una Client Assertion che consente di
identificare il RP che esegue la richiesta.

**Esempio:**

+-----------------------+-----------------------+-----------------------+
| *POST                 |                       |                       |
| https://op.spid.agid. |                       |                       |
| gov.it/revoke?*       |                       |                       |
|                       |                       |                       |
| | **client_assertion* |                       |                       |
| *\ =eyJhbGciOiJIUzI1N |                       |                       |
| iIsInR5cCI6IkpXVCJ9.e |                       |                       |
| yJzdWIiOiIxMjM0NTY3OD |                       |                       |
| kwIiwibmFtZSI6IlNQSUQ |                       |                       |
| iLCJhZG1pbiI6dHJ1ZX0. |                       |                       |
| LVyRDPVJm0S9q7oiXcYVI |                       |                       |
| IqGWY0wWQlqxvFGYswLF8 |                       |                       |
| 8&                    |                       |                       |
| | **client_assertion_ |                       |                       |
| type**\ =urn%3Aietf%3 |                       |                       |
| Aparams%3Aoauth%3Acli |                       |                       |
| ent-assertion-type%3A |                       |                       |
| jwt-bearer&           |                       |                       |
| | **client_id**\ =htt |                       |                       |
| ps%3A%2F%2Frp.spid.ag |                       |                       |
| id.gov.it&\ **        |                       |                       |
|   token**\ =eyJhbGciO |                       |                       |
| iJSUzI1NiJ9.eyJleHAiO |                       |                       |
| jE0MTg3MDI0MTQsImF1ZC |                       |                       |
| I6WyJlNzFmYjcyYS05NzR |                       |                       |
| mLTQwMDEtYmNiNy1lNjdj |                       |                       |
| MmJjMDAzN2YiXSwiaXNzI |                       |                       |
| joiaHR0cHM6XC9cL2FzLX |                       |                       |
| ZhLmV4YW1wbGUuY29tXC8 |                       |                       |
| iLCJqdGkiOiIyMWIxNTk2 |                       |                       |
| ZC04NWQzLTQzN2MtYWQ4M |                       |                       |
| y1iM2YyY2UyNDcyNDQiLC |                       |                       |
| JpYXQiOjE0MTg2OTg4MTR |                       |                       |
| 9.FXDtEzDLbTHzFNroW7w |                       |                       |
| 27RLk5m0wprFfFH7h4bdF |                       |                       |
| w5fR3pwiqejKmdfAbJvN3 |                       |                       |
| _yfAokBv06we5RARJUbdj |                       |                       |
| mFFfRRW23cMbpGQCIk7Nq |                       |                       |
| 4L012X_1J4IewOQXXMLTy |                       |                       |
| WQQ_BcBMjcW3MtPrY1AoO |                       |                       |
| cfBOJPx1k2jwRkYtyVTLW |                       |                       |
| lff6S5gK-ciYf3b0bAdjo |                       |                       |
| QEHd_IvssIPH3xuBJkmtk |                       |                       |
| rTlfWR0Q0pdpeyVePkMSI |                       |                       |
| 28XZvDaGnxA4j7QI5loZY |                       |                       |
| eyzGR9h70xQLVzqwwl1P0 |                       |                       |
| -F_0JaDFMJFO1yl4Iexfp |                       |                       |
| oZZsB3HhF2vFdL6D_lLeH |                       |                       |
| Ry-H2g2OzF59eMIsM_Ccs |                       |                       |
| 4G47862w              |                       |                       |
+-----------------------+-----------------------+-----------------------+
| **Parametro**         | **Descrizione**       | **Valori ammessi**    |
+-----------------------+-----------------------+-----------------------+
| **client_assertion**  | JWT firmato con la    | L’OP deve verificare  |
|                       | chiave privata del    | la validità di tutti  |
|                       | Relying Party         | i campi presenti nel  |
|                       | contenente gli stessi | JWT, nonché la        |
|                       | parametri documentati | validità della sua    |
|                       | per le richieste al   | firma in relazione al |
|                       | Token Endpoint.       | parametro             |
|                       |                       | **client_id**.        |
+-----------------------+-----------------------+-----------------------+
| **client_assertion_ty |                       | **urn:ietf:params:oau |
| pe**                  |                       | th:client-assertion-t |
|                       |                       | ype:jwt-bearer**      |
+-----------------------+-----------------------+-----------------------+
| **client_id**         | URI che identifica    | L’OP deve verificare  |
|                       | univocamente il RP    | che il client_id sia  |
|                       | come da Registro      | noto.                 |
|                       | SPID.                 |                       |
+-----------------------+-----------------------+-----------------------+
| **Token**             | Il token su cui il RP |                       |
|                       | vuole ottenere        |                       |
|                       | informazioni.         |                       |
+-----------------------+-----------------------+-----------------------+
