Generazione del code_challenge per PKCE
=======================================

PKCE (Proof Key for Code Exchange,
`RFC7636 <https://tools.ietf.org/html/rfc7636>`__) è un’estensione del
protocollo OAuth 2.0 finalizzata ad evitare un potenziale attacco
attuato con l’intercettazione dell’authorization code, soprattutto nel
caso di applicazioni per dispositivi mobili. Consiste nella generazione
di un codice (*code verifier*) e del suo hash (*code challenge*). Il
*code challenge* viene inviato all’OP nella richiesta di autenticazione.

Quando il client contatta il Token Endpoint al termine del flusso di
autenticazione, invia il *code verifier* originariamente creato, in modo
che l’OP possa confrontare che il suo hash corrisponda con quello
acquisito nella richiesta di autenticazione.

Il *code verifier* deve avere una lunghezza compresa tra 43 e 128
caratteri e deve essere generato con un algoritmo crittografico ad alta
entropia.

Il *code challenge* deve essere generato con algoritmo SHA256.

**Riferimenti:**

+--------------------------------------------------------------------------+
| http://openid.net/specs/openid-igov-oauth2-1_0-02.html#rfc.section.3.1.7 |
|                                                                          |
| https://tools.ietf.org/html/rfc7636                                      |
+--------------------------------------------------------------------------+

.. forum_italia::
   :topic_id: 10921
   :scope: document
