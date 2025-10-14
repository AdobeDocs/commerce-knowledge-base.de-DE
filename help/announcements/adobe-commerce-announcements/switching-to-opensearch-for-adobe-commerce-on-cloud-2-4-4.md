---
title: Wechseln zu OpenSearch für Adobe Commerce in Cloud 2.4.4
promoted: true
description: Adobe Commerce auf Cloud-Infrastruktur 2.4.4 unterstützt nach Version 7.10 keine Elasticsearch-Versionen mehr. **Sie müssen zuerst ein Upgrade auf Adobe Commerce 2.4.4 durchführen und dann sofort vom Elasticsearch auf OpenSearch 1.2.x wechseln.** Adobe enthält detaillierte Anweisungen näher an der Adobe Commerce-Version 2.4.4 GA.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Wechseln zu OpenSearch für Adobe Commerce in Cloud 2.4.4

Adobe Commerce auf Cloud-Infrastruktur 2.4.4 unterstützt keine Elasticsearch-Versionen nach 7.10. **Sie müssen zuerst auf Adobe Commerce 2.4.4 aktualisieren und dann sofort vom Elasticsearch zu OpenSearch 1.2.x wechseln.** Die Adobe enthält detaillierte Anweisungen näher an der Adobe Commerce-Version 2.4.4 GA.

>[!NOTE]
>
>Der Wechsel sollte unabhängig vom Cloud-Anbieter erfolgen.

Adobe Commerce On-Premise fügt Unterstützung für Elasticsearch 7.16 und OpenSearch 1.2 in allen Patch-Versionen vom März 2022 hinzu (2.4.4, 2.4.3-p2 und 2.3.7-p3). In Version 2.4.4 wird Adobe Commerce in der Cloud-Infrastruktur auf OpenSearch als Standard-Suchmaschine umgestellt, sodass Händler OpenSearch anstelle von Elasticsearch verwenden müssen, bevor sie ein Upgrade auf Adobe Commerce 2.4.4 oder höher durchführen. Händler mit lokalen Adobe Commerce-Bereitstellungen können Elasticsearch oder OpenSearch verwenden, da Adobe Commerce weiterhin beide unterstützt.


## Was ist OpenSearch?

OpenSearch ist eine Abspaltung aus Elasticsearch und Kibana. Es wird von AWS statt von Elastic.co gepflegt. Weitere Informationen finden Sie unter GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Kompatibilität zwischen Versionen:**

**Unterstützt Adobe Commerce auf Cloud-Infrastruktur Elasticsearch 7.10?**

**Ja** - Ab Mitte Januar 2022 unterstützen die Adobe Commerce on Cloud Infrastructure-Versionen 2.4.3-p1, 2.4.3-p2 und 2.3.7-p3 das Elasticsearch 7.10.

Bei lokalen Adobe Commerce-Installationen wird die neueste Version 7.16.x empfohlen, um das Risiko von Log4j zu verringern.

## Migration:

## Wann können Händler zu OpenSearch migrieren?

Nach Adobe Commerce 2.4.4.

Bevor Sie mit dem Upgrade auf Adobe Commerce 2.4.4 beginnen, müssen Händler jedoch eine aktuelle Version von Adobe Commerce verwenden, die Elasticsearch 7.10 unterstützt, und mindestens ein Elasticsearch haben, bevor Sie mit dem Upgrade auf Adobe Commerce 2.4.4 oder OpenSearch beginnen.

## Was können Händler (Adobe Commerce auf Cloud-Infrastruktur und Adobe Commerce On-Premise) tun, die nicht auf Version 2.4.4 basieren? Können sie auf eine unterstützte Version von Elasticsearch (7.10, 7.16.1) oder auf OpenSearch aktualisieren? Müssen sie hierfür die neueste unterstützte Version verwenden (z. B. 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)?

Wenn die Adobe Commerce-Kernversion, auf der sie sich befinden, Elasticsearch 7.10 unterstützt, können sie sie verwenden.

Informationen [&#x200B; Versionskompatibilität finden Sie in &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=de) Entwicklerdokumentation unter „Systemanforderungen“.

>[!NOTE]
>
>Es wird empfohlen, so bald wie möglich ein Upgrade auf Adobe Commerce 2.4.4 zu planen, da Elasticsearch 7.10 im Mai 2022 auslaufen wird.

Adobe-Partner können sich für unser Beta-Programm [hier](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html?lang=de) anmelden, um Zugang zu unserem neuesten Beta4-Code zu erhalten, der gegen Elasticsearch 7.16.1 und OpenSearch 1.1 getestet wurde.
