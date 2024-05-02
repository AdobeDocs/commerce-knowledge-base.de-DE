---
title: "ACSD-52657: Minicart wird im zweiten Speicher, der Subdomain verwendet, nicht aktualisiert."
description: Wenden Sie den Patch ACSD-52657 an, um das Adobe Commerce-Problem zu beheben, bei dem der Minicart beim zweiten Store, der eine Subdomain verwendet, nicht aktualisiert wird.
feature: Shopping Cart
role: Admin, Developer
exl-id: d0877a15-800e-4e10-9ace-ebb7f26dbd18
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-52657: Minicart wird beim zweiten Store, der die Subdomain verwendet, nicht aktualisiert

Der Patch ACSD-52657 behebt das Problem, bei dem der Minicart im zweiten Speicher, der eine Subdomain verwendet, nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 ist installiert. Die Patch-ID ist ACSD-52657. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Minicart wird im sekundären Speicher, der eine Subdomain verwendet, nicht aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen zweiten Store und konfigurieren Sie eine Subdomain für die Basis-URL.
1. Aktualisieren Sie die Cookie-Domäne auf die allgemeine Domäne.
1. Fügen Sie im Hauptspeicher ein Produkt zum Warenkorb hinzu.
1. Aktualisieren Sie den zweiten Storebericht und navigieren Sie dann zur Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb und der Minicart werden in der Subdomain aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Minicart wird nicht aktualisiert, wenn der sekundäre Store aktualisiert wird, aber die Warenkorbseite zeigt das hinzugefügte Produkt an und Sie können in dieser Sitzung eine Bestellung aufgeben (`PHPSESSID` -Cookie freigegeben ist).

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
