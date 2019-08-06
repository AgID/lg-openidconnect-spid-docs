Applicazioni per dispositivi mobili
===================================

Nel caso di applicazioni mobili rimane il requisito di seguire
l’Authorization Code Flow descritto sopra.

In tale contesto, nel diagramma di cui al paragrafo precedente,
l’elemento identificato come Relying Party sta ad identificare l’insieme
della applicazione residente sul dispositivo mobile e del suo eventuale
backend.

Le richieste al Token Endpoint e allo UserInfo Endpoint possono pertanto
essere inviate sia dall’applicazione sia dal suo backend; lo scambio di
informazioni tra l’applicazione mobile e il suo eventuale backend non
sono normate dal presente documento, ferma restando la raccomandazione
di prevedere meccanismi di trasmissione e archiviazione sicuri che
impediscano a terze parti di venire in possesso dell’Access Token.

Per inviare la Authentication Request all’OP è possibile usare il
browser o una webview, purché protetta con i meccanismi più sicuri messi
a disposizione dai sistemi operativi al fine di ottenere il massimo
isolamento dall’applicazione chiamante. A tal fine si consiglia l’uso
della libreria AppAuth e si rinvia alle indicazioni contenute nelle
Linee Guida User Experience SPID.

Si rimanda a `RFC8252 <https://tools.ietf.org/html/rfc8252>`__ per
ulteriori specifiche tecniche e raccomandazioni di sicurezza da
applicarsi in caso di applicazioni mobili.

**Riferimenti**

+-----------------------------------------------------------------------+
| `RFC8252: OAuth 2.0 for Native Apps                                   |
| (https://tools.ietf.org/html/rfc8252) <https://tools.ietf.org/html/rf |
| c8252>`__                                                             |
+-----------------------------------------------------------------------+
