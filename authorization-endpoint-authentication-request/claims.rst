Claims
======

Il parametro claims definisce gli attributi e il livello SPID richiesti.
all’interno dell’elemento "*userinfo*" si elencano gli attributi, da
richiedere come chiavi di oggetti JSON, i cui valori devono essere
*null*. Gli attributi elencati sotto "userinfo" sono disponibili al
momento della chiamata allo UserInfo Endpoint.

.. code-block:: json

  {
   "userinfo": 
    {
     "https://attributes.spid.gov.it/familyName": 
      {
       "essential": true
      }
    },
  }                                                             

Se il Relying Party è privato, gli OpenID Provider devono controllare
che gli attributi richiesti rientrino tra quelli che essi, in base alla
convenzione, possono utilizzare.

**Riferimenti:**

+-------------------------------------------------------------------------------+
| http://openid.net/specs/openid-connect-core-1_0.html#IndividualClaimsRequests |                                                         
+-------------------------------------------------------------------------------+

.. forum_italia::
   :topic_id: 10920
   :scope: document
