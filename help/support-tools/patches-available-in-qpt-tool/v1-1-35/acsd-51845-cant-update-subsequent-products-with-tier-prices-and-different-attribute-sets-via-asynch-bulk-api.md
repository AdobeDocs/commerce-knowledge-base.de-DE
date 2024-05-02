---
title: "ACSD-51845: Nachfolgende Produkte können nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrone Bulk aktualisiert werden [!DNL API]"
description: Wenden Sie den Patch ACSD-51845 an, um das Adobe Commerce-Problem zu beheben, bei dem Sie nachfolgende Produkte nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrone Massen aktualisieren können. [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: Nachfolgende Produkte können nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrone Bulk aktualisiert werden [!DNL API]

Der Patch ACSD-51845 behebt das Problem, dass Sie nachfolgende Produkte nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrone Massen aktualisieren können [!DNL REST API]. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51845. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Aktualisierung schlägt für nachfolgende Produkte mit Stufenpreisen und verschiedenen Attributsätzen über asynchrones Massen fehl [!DNL REST API].

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren [!DNL RabbitMQ].
1. Erstellen Sie zwei Attributsätze.
1. Erstellen Sie zwei **Einfache Produkte**, wodurch jedes Produkt einem anderen Attributsatz zugewiesen wird.
1. Hinzufügen einer **Preis der Kundengruppe** für jedes Produkt.
1. Aktualisieren Sie beide Produkte in derselben Menge [!DNL API] aktualisieren.
1. Stellen Sie sicher, dass die Variable `bin/magento queue:consumers:start async.operations.all` ausgeführt wird.
1. Massenüberprüfung [!DNL API] -Status.

<u>Erwartete Ergebnisse</u>:

Die Ausführung des Dienstes ist erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Das System gibt die Fehlermeldung zurück: *Das Produkt konnte nicht gespeichert werden. Bitte versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
