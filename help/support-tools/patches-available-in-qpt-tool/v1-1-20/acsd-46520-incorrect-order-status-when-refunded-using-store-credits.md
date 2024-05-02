---
title: "ACSD-46520: Falscher Bestellstatus bei Rückerstattung mittels Gutschriften für Geschäfte"
description: Dieser Artikel bietet eine Lösung für das Problem, dass Benutzer einen falschen Bestellstatus erhalten, wenn sie mit Store-Gutschriften zurückerstattet werden.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: Unrichtiger Bestellstatus bei Rückerstattung mittels Gutschriften für Geschäfte

Der Patch ACSD-46520 löst das Problem, dass Benutzer einen falschen Bestellstatus erhalten, wenn sie mit Store-Gutschriften zurückerstattet werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46520. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten einen falschen Bestellstatus, wenn sie mit Gutschriften zurückerstattet werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Kundenkonto in der Storefront und melden Sie sich an.
1. Weisen Sie dem Kunden vom Administrator Store-Gutschriften zu. Die Gutschriften aus dem Geschäft sollten die gesamte Bestellung abdecken.
1. Bestellung unter Verwendung der Gutscheine.
1. Rechnungsstellung.
1. Erstellen Sie ein Kreditmemo, um den vollen Betrag der Bestellung zurückzuerstatten.
Wählen Sie die **[!UICONTROL Refund to store credit]** aktivieren.
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Bestellstatus lautet *Geschlossen*.

<u>Tatsächliche Ergebnisse</u>:

Der Bestellstatus lautet *Fertig*, der nicht den korrekten Status aufweist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder [!DNL Magento Open Source] vor Ort: [Tools für Qualitätsmuster > Verwendung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch &quot;Qualitätsmuster-Tool&quot;.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch &quot;Qualitätsmuster-Tool&quot;.
