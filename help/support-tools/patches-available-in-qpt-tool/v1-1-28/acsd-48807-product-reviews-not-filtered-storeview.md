---
title: "ACSD-48807: Produktüberprüfungen nicht nach Storebericht gefiltert"
description: Wenden Sie den Patch ACSD-48807 an, um das Adobe Commerce-Problem zu beheben, bei dem Produktüberprüfungen nicht durch die Storeübersicht über GraphQL gefiltert werden.
exl-id: 754ef455-ff06-4832-9eb6-ad8cccec8799
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48807: Produktüberprüfungen nicht nach Storebericht gefiltert

Der Patch ACSD-48807 behebt das Problem, dass Produktübersichten nicht durch die Storeübersicht über GraphQL gefiltert werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 ist installiert. Die Patch-ID lautet ACSD-48807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produktüberprüfungen werden nicht nach Storebericht über GraphQL gefiltert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen zusätzlichen Store.
1. Erstellen Sie ein Kundenkonto und melden Sie sich an.
1. Erstellen Sie im Standardspeicher eine Überprüfung für ein Produkt.
1. Wechseln Sie zu einem anderen Store und erstellen Sie eine weitere Überprüfung für ein Produkt.
1. Genehmigen Sie beide Überprüfungen in Adobe Commerce Admin.
1. Senden Sie eine GraphQL-Kundenabfrage, um Produktüberprüfungen abzurufen, während Sie die in Schritt 1 in der Kopfzeile erstellte Storeüberprüfung angeben.
1. Beobachten Sie die Antwort.

<u>Erwartete Ergebnisse</u>:

In der Antwort wird nur die Produktüberprüfung für den angegebenen Store zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Beide Überprüfungen werden in der Antwort zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
