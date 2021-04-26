Standard di riferimento
=======================

SPID OpenID Connect è basato sul profilo iGov (openid-gov-profile) di
OpenID Connect, *International Government Assurance Profile (iGov) for
OpenID Connect 1.0*, con la seguente personalizzazione:

-  paragrafo 4,2 di openid-igov-openid-connect-1_0: Scope: viene
   utilizzato sempre lo scope "openid" e viene consigliato l'uso
   di "profile" per l'ottenimento del set esteso degli attributi utente.
   Altri scopi possono essere ad esempio utilizzati per estendere
   le finalità della richiesta di autorizzazione, come definito nello
   standard OAuth2 sebbene questi non riguardino il profilo OIDC SPID;

-  paragrafo 3,7 e 2,5 di openid-igov-openid-connect-1_0: I metadata
   degli attori sono distribuiti secondo le modalità definite
   dall’Agenzia per l’Italia Digitale.

**Riferimenti**

+------------------------------------------------------------------+
| https://openid.net/specs/openid-igov-openid-connect-1_0-ID1.html |
|                                                                  |
| http://openid.net/specs/openid-igov-oauth2-1_0-02.html           |
+------------------------------------------------------------------+

.. forum_italia::
   :topic_id: 10912
   :scope: document
