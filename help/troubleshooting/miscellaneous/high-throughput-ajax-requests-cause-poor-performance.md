---
title: AJAX-Anfragen mit hohem Durchsatz führen zu schlechter Leistung
description: Dieser Artikel bietet eine Lösung für Leistungsprobleme mit Adobe Commerce On-Premise oder Adobe Commerce auf Cloud-Infrastruktur-Sites aufgrund einiger Anfragen mit hohem Durchsatz, die zu erheblicher Server-Last und Traffic führen.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 3bcdbd0536ec71cb80ffa3afbcd53c4ae385d2e3
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# AJAX-Anfragen mit hohem Durchsatz führen zu schlechter Leistung

Dieser Artikel bietet eine Lösung für Leistungsprobleme mit Adobe Commerce On-Premise oder Adobe Commerce auf Cloud-Infrastruktur-Sites aufgrund einiger Anfragen mit hohem Durchsatz, die zu erheblicher Server-Last und Traffic führen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premises 2.2.x, 2.3.x

>[!NOTE]
>
>Das Problem wurde in Version 2.3.4 sowohl von Adobe Commerce on Cloud Infrastructure als auch von Adobe Commerce On-Premise behoben.

### Problem

Die Site weist aufgrund von Anfragen mit hohem Durchsatz, wie kritischen AJAX-Anfragen, eine langsame Leistung auf.

### Ursache

AJAX-Anfragen mit hohem Durchsatz beziehen sich auf diejenigen, die mit den privaten Inhalten der Kunden zusammenhängen.

### Lösung

Es gibt drei Lösungen:

* [Aktualisieren Sie auf Version 2.3.4](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Stellen Sie leichtere Anfragen sicher (Cache-Anfragen oder Verschieben in den privaten Inhalt von Kunden).
* Reduzieren Sie die Anzahl der Anfragen.

<u>Stellen Sie leichtere Anfragen sicher (Cache-Anfragen oder Verschieben in private Inhalte von Kunden)</u>

Wenn auf jeder Seite AJAX-Anfragen von Drittanbietern ausgelöst werden, versuchen Sie, diese Anfragen zwischenzuspeichern oder in den privaten Inhalt der Kunden zu verschieben. Der Händler kann dies tun, indem er sicherstellt, dass benutzerdefinierte AJAX-Anfragen mit den GET-HTTP-Methoden aufgerufen werden. Dadurch können diese Anfragen von Fastly zwischengespeichert werden. Wenn es benutzerdefinierte AJAX-Anfragen gibt, die nicht zwischengespeichert werden sollen, sollten sie gemäß der Funktion für private Inhalte umgestaltet werden. Anweisungen hierzu finden Sie [Privater Inhalt](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in unserer Entwicklerdokumentation.

<u>Reduzieren Sie die Anzahl der Anfragen</u>

* Deaktivieren Sie den beständigen Warenkorb, da er die Anzahl der `customer/section/load` Anfragen erhöhen kann. Befolgen Sie die Schritte unter [Pfade zum beständigen Warenkorb](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/paths/config-reference-general) in unserer Entwicklerdokumentation, um zu sehen, ob der beständige Warenkorb aktiviert ist.
* Wenn Sie Inhalte in neu laden oder ungültig machen müssen, befolgen Sie `sections.xml` Schritte unter [Privater Inhalt: Invalidierung privater Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie die `customerData.reload()`-Methode nicht direkt in Ihren Anpassungen verwenden.
* Überprüfen Sie andere POST-AJAX-Anfragen auf derselben Seite. Öffnen Sie das Google Chrome-Entwickler-Tool im Google Chrome-Browser. Klicken Sie auf **Registerkarte** und dann auf die Registerkarte **XHR**. Daraufhin wird eine Liste aller AJAX-Anfragen von der jeweiligen Seite angezeigt. Klicken Sie dann auf jede Anfrage. Im Feld Anfragemethode sollten die GET-Anfragen angezeigt werden. Hinweis: Google Chrome wird als Beispiel verwendet. Dies ist auch in anderen Browsern möglich.
* Überprüfen Sie die Funktion von Google Tag Manager (GTM), die eine bestimmte AJAX-Anfrage ist. Der Benutzer kann diese AJAX entfernen und ihre Anpassung mit privater Funktion refaktorieren, um die Gesamtzahl der Anfragen an den Server zu reduzieren.
* Überprüfen Sie, ob das Adobe Commerce-Banner aktiviert, aber nicht verwendet ist. Möglicherweise müssen Sie [Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### Verwandtes Lesen

Weitere Informationen zu Inhalten privater Kunden finden Sie unter [Private Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in unserer Entwicklerdokumentation.
