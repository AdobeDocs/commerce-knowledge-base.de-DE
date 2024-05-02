---
title: Wechseln zu OpenSearch für Adobe Commerce in Cloud 2.4.4
promoted: true
description: Adobe Commerce in der Cloud-Infrastruktur 2.4.4 unterstützt keine Versionen von Elasticsearch nach 7.10. **Sie müssen zuerst auf Adobe Commerce 2.4.4 aktualisieren und dann sofort von Elasticsearch zu OpenSearch 1.2.x wechseln.** Adobe bietet detaillierte Anweisungen, die näher an der Adobe Commerce-Version 2.4.4 GA liegen.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Wechseln zu OpenSearch für Adobe Commerce in Cloud 2.4.4

Adobe Commerce in der Cloud-Infrastruktur 2.4.4 unterstützt keine Versionen von Elasticsearch nach 7.10. **Sie müssen zuerst auf Adobe Commerce 2.4.4 aktualisieren und dann sofort von Elasticsearch zu OpenSearch 1.2.x wechseln.** Adobe stellt detaillierte Anweisungen zur Adobe Commerce 2.4.4 GA-Version bereit.

>[!NOTE]
>
>Der Wechsel sollte unabhängig vom Cloud-Anbieter erfolgen.

Adobe Commerce On-Premise unterstützt nun Elasticsearch 7.16 und OpenSearch 1.2 in allen Patch-Versionen vom März 2022 (2.4.4, 2.4.3-p2 und 2.3.7-p3). In Version 2.4.4 wird Adobe Commerce in der Cloud-Infrastruktur als Standardsuchmaschine zu OpenSearch verschoben. Daher müssen Händler OpenSearch anstelle von Elasticsearch verwenden, bevor sie auf Adobe Commerce 2.4.4 oder höher aktualisieren. Merchants mit lokalen Adobe Commerce-Bereitstellungen von können Elasticsearch oder OpenSearch verwenden, da Adobe Commerce beide weiterhin unterstützt.


## Was ist OpenSearch?

OpenSearch ist eine Gabel von Elasticsearch und Kibana. Sie wird von AWS statt von Elastic.co verwaltet. Weitere Informationen finden Sie unter GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Versionsübergreifende Kompatibilität:**

**Unterstützt Adobe Commerce on Cloud Infrastructure Elasticsearch 7.10?**

**Ja** - Ab Mitte Januar 2022 unterstützt Adobe Commerce die Cloud-Infrastrukturversionen 2.4.3-p1, 2.4.3-p2 und 2.3.7-p3 Elasticsearch 7.10.

Für Adobe Commerce vor Ort wird die neueste Version 7.16.x empfohlen, um Log4j zu minimieren.

## Migration:

## Wann können Händler zu OpenSearch migrieren?

Nach Adobe Commerce 2.4.4.

Bevor Sie mit dem Upgrade-Prozess auf Adobe Commerce 2.4.4 beginnen, müssen sich die Händler jedoch auf einer aktuellen Version von Adobe Commerce befinden, die Elasticsearch 7.10 unterstützt, und sich mindestens auf einem Elasticsearch befinden, bevor Sie mit dem Upgrade-Prozess auf Adobe Commerce 2.4.4 oder OpenSearch beginnen.

## Was können Händler (Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort), die nicht unter 2.4.4 sind, tun? Können sie auf eine unterstützte Version von Elasticsearch (7.10, 7.16.1) oder auf OpenSearch aktualisieren? Müssen sie die neueste unterstützte Version verwenden, um dies zu tun (z. B. 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)?

Wenn die Adobe Commerce-Kernversion, in der sie verwendet wird, Elasticsearch 7.10 unterstützt, kann sie verwendet werden.

Überprüfen [Systemanforderungen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) in unserer Entwicklerdokumentation zur Versionskompatibilität.

>[!NOTE]
>
>Es wird empfohlen, so bald wie möglich ein Upgrade auf Adobe Commerce 2.4.4 zu planen, da Elasticsearch 7.10 im Mai 2022 als EOL eingestellt wird.

Adobe-Partner können sich für unser Betaprogramm registrieren [here](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html) um Zugriff auf unseren neuesten Beta4-Code zu erhalten, der mit Elasticsearch 7.16.1 und OpenSearch 1.1 getestet wurde.
