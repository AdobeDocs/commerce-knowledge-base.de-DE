---
title: "ACSD-51102: Katalogregel, die auf eine große Anzahl von nicht korrekt indizierten Produkten angewendet wird"
description: Wenden Sie den Patch ACSD-51102 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht richtig indiziert wird, wenn die Regel durch eine geplante Aktualisierung aktiviert wird.
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102: Katalogregel angewendet auf eine große Anzahl von Produkten nicht korrekt indiziert

Der Patch ACSD-51102 behebt das Problem, dass eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht richtig indiziert wird, wenn die Regel durch eine geplante Aktualisierung aktiviert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51102. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, wird nicht korrekt indiziert, wenn die Regel durch eine geplante Aktualisierung aktiviert wird.

Voraussetzungen:

* Cron-Auftrag wird eingerichtet und jede Minute ausgeführt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen großen Katalog mit Tausenden von Produkten, um die Laufzeit für die *Katalogregel*-Indexer von mehr als 120 Sekunden zu erreichen, wenn Katalogregeln aktiviert werden.
2. Erstellen Sie zwei Katalogregeln mit dem Status *Aktiv* , der auf *Nein* festgelegt ist.  Beispiel: *Test 1* und *Test 2*. Jede Regel sollte sich auf alle Produkte im Katalog auswirken und dazu führen, dass der Indexer länger als 120 Sekunden ausgeführt wird.
3. Stellen Sie sicher, dass der Status des Indexers *Bereit* ist.
4. Erstellen Sie geplante Aktualisierungen, um diese beiden Regeln zu aktivieren. *Test 2* sollte kurz nach *Test 1* beginnen. Beispiel: mit einer 1-minütigen Differenz.
5. Überprüfen Sie die Produktpreise an der Storefront.

<u>Erwartete Ergebnisse</u>

Es werden Rabatte von beiden Regeln angewendet.

<u>Tatsächliche Ergebnisse</u>

Es wird nur der Rabatt der ersten Regel angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
