.. _request-1:

Request
=======

La richiesta all’Introspection Endpoint consiste nell’invio del token su
cui si vogliono ottenere informazioni unitamente ad una Client Assertion
che consente di identificare il RP che esegue la richiesta.

**Esempio:**

+-----------------------------------------------------------------------+
| *POST https://op.spid.agid.gov.it/introspection?*                     |
|                                                                       |
| | **client_assertion**\ =eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWI |
| iOiIxMjM0NTY3ODkwIiwibmFtZSI6IlNQSUQiLCJhZG1pbiI6dHJ1ZX0.LVyRDPVJm0S9 |
| q7oiXcYVIIqGWY0wWQlqxvFGYswLF88&                                      |
| | **client_assertion_type**\ =urn%3Aietf%3Aparams%3Aoauth%3Aclient-as |
| sertion-type%3Ajwt-bearer&                                            |
| | **client_id**\ =https%3A%2F%2Frp.spid.agid.gov.it&\ **              |
|   token**\ =eyJhbGciOiJSUzI1NiJ9.eyJleHAiOjE0MTg3MDI0MTQsImF1ZCI6WyJl |
| NzFmYjcyYS05NzRmLTQwMDEtYmNiNy1lNjdjMmJjMDAzN2YiXSwiaXNzIjoiaHR0cHM6X |
| C9cL2FzLXZhLmV4YW1wbGUuY29tXC8iLCJqdGkiOiIyMWIxNTk2ZC04NWQzLTQzN2MtYW |
| Q4My1iM2YyY2UyNDcyNDQiLCJpYXQiOjE0MTg2OTg4MTR9.FXDtEzDLbTHzFNroW7w27R |
| Lk5m0wprFfFH7h4bdFw5fR3pwiqejKmdfAbJvN3_yfAokBv06we5RARJUbdjmFFfRRW23 |
| cMbpGQCIk7Nq4L012X_1J4IewOQXXMLTyWQQ_BcBMjcW3MtPrY1AoOcfBOJPx1k2jwRkY |
| tyVTLWlff6S5gK-ciYf3b0bAdjoQEHd_IvssIPH3xuBJkmtkrTlfWR0Q0pdpeyVePkMSI |
| 28XZvDaGnxA4j7QI5loZYeyzGR9h70xQLVzqwwl1P0-F_0JaDFMJFO1yl4IexfpoZZsB3 |
| HhF2vFdL6D_lLeHRy-H2g2OzF59eMIsM_Ccs4G47862w                          |
+-----------------------------------------------------------------------+

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
| **client_assertion_ty |                       | -  **urn:ietf:params: |
| pe**                  |                       | oauth:client-assertio |
|                       |                       | n-type:jwt-bearer**   |
+-----------------------+-----------------------+-----------------------+
| **client_id**         | URI che identifica    | L’OP deve verificare  |
|                       | univocamente il RP    | che il client_id sia  |
|                       | come da Registro      | noto.                 |
|                       | SPID.                 |                       |
+-----------------------+-----------------------+-----------------------+
| **token**             | Il token su cui il RP |                       |
|                       | vuole ottenere        |                       |
|                       | informazioni.         |                       |
+-----------------------+-----------------------+-----------------------+
