---
title: Hohe Durchsatzraten AJAX Anforderungen führen zu schlechter Leistung
description: Dieser Artikel bietet eine Lösung für Leistungsprobleme mit Adobe Commerce On-Premise oder Adobe Commerce auf Cloud-Infrastruktur-Sites, da einige Anforderungen mit hohem Durchsatz zu beträchtlicher Serverlast und Traffic führen.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Hohe Durchsatzraten AJAX Anforderungen führen zu schlechter Leistung

Dieser Artikel bietet eine Lösung für Leistungsprobleme mit Adobe Commerce On-Premise oder Adobe Commerce auf Cloud-Infrastruktur-Sites, da einige Anforderungen mit hohem Durchsatz zu beträchtlicher Serverlast und Traffic führen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

>[!NOTE]
>
>Das Problem wurde in Version 2.3.4 von Adobe Commerce in der Cloud-Infrastruktur und in Adobe Commerce vor Ort behoben.

### Problem

Die Leistung der Site ist aufgrund von Anforderungen mit hohem Durchsatz, wie z. B. kritischen AJAX, langsam.

### Ursache

Zu den Anforderungen mit hohem Durchsatz AJAX Anforderungen gehören Anforderungen im Zusammenhang mit privaten Inhalten von Kunden.

### Lösung

Es gibt drei Lösungen:

* [Aktualisieren Sie auf Version 2.3.4](https://devdocs.magento.com/cloud/project/project-upgrade.html). Wenn dies derzeit nicht möglich ist, installieren Sie [den Patch, der das Problem behebt](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* Stellen Sie leichtere Anforderungen sicher (Cache-Anforderungen oder Wechsel zum privaten Inhalt von Kunden).
* Reduzieren Sie die Anzahl der Anforderungen.

<u>Sicherstellen von leichteren Anforderungen (Cache-Anforderungen oder Wechsel zum privaten Inhalt von Kunden)</u>

Wenn auf jeder Seite AJAX Anforderungen von Drittanbietern ausgelöst werden, versuchen Sie, diese Anforderungen zwischenzuspeichern oder in den privaten Inhalt des Kunden zu verschieben. Der Händler kann dies tun, indem er sicherstellt, dass benutzerdefinierte AJAX-Anfragen mithilfe der GET-HTTP-Methoden aufgerufen werden. Dadurch werden diese Anfragen von Fastly zwischenspeicherbar. Wenn es benutzerdefinierte AJAX-Anforderungen gibt, die nicht zwischengespeichert werden sollen, sollten sie entsprechend der Funktion für private Inhalte umstrukturiert werden. Anweisungen finden Sie unter [Private Inhalte](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) in unserer Entwicklerdokumentation.

<u>Reduzieren der Anzahl der Anforderungen</u>

* Deaktivieren Sie den beständigen Warenkorb, da dadurch die Anzahl der `customer/section/load` -Anfragen erhöht werden kann. Führen Sie die Schritte unter [Persistente Einkaufswagenpfade](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) in unserer Entwicklerdokumentation aus, um zu sehen, ob der beständige Warenkorb aktiviert ist.
* Wenn Sie Inhalte in `sections.xml` neu laden oder ungültig machen müssen, führen Sie die Schritte unter [Privater Inhalt: Ungültiges privates Inhalt](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) in unserer Entwicklerdokumentation aus. Stellen Sie sicher, dass Sie die `customerData.reload()` -Methode nicht direkt in Ihren Anpassungen verwenden.
* Überprüfen Sie andere POST AJAX Anforderungen auf derselben Seite. Öffnen Sie das Google Chrome-Entwickler-Tool im Google Chrome-Browser. Klicken Sie auf die Registerkarte &quot;**Netzwerk**&quot;und dann auf die Registerkarte &quot;**XHR**&quot;. Daraufhin wird eine Liste aller AJAX Anforderungen von der jeweiligen Seite angezeigt. Klicken Sie dann auf jede Anforderung und im Feld Anforderungsmethode sollten die GET-Anforderungen angegeben werden. Hinweis: Google Chrome wird als Beispiel verwendet. Dies ist auch in anderen Browsern möglich.
* Überprüfen Sie die Google Tag Manager (GTM)-Funktionalität, bei der es sich um eine bestimmte AJAX handelt. Der Benutzer kann diese AJAX entfernen und seine Anpassung durch private Funktionen umgestalten, um die Gesamtzahl der Anforderungen an den Server zu reduzieren.
* Überprüfen Sie, ob das Adobe Commerce-Banner aktiviert, aber nicht verwendet ist. Möglicherweise müssen Sie [Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### Verwandte Informationen

Weitere Informationen zu Inhalten privater Kunden finden Sie unter [Private Inhalte](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) in unserer Entwicklerdokumentation.
