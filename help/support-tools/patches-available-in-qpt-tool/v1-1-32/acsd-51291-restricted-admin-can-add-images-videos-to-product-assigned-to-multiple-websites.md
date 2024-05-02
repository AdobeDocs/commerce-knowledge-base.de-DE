---
title: "ACSD-51291: Eingeschränkte Administratoren können Bildern/Videos zu Produkten hinzufügen, die mehreren Websites zugewiesen sind"
description: Wenden Sie den Patch ACSD-51291 an, um das Adobe Commerce-Problem zu beheben, bei dem eingeschränkte Administratoren mit Zugriff auf eine Website Bilder/Videos zu einem Produkt hinzufügen können, das mehreren Websites zugewiesen ist.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: Eingeschränkte Administratoren können Bildern/Videos zu Produkten hinzufügen, die mehreren Websites zugewiesen sind

Der Patch ACSD-51291 behebt das Problem, dass ein eingeschränkter Administrator mit Zugriff auf eine Website Bilder/Videos zu einem Produkt hinzufügen kann, das mehreren Websites zugewiesen ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51291. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein eingeschränkter Administrator mit Zugriff auf eine Website kann einem Produkt, das mehreren Websites zugewiesen ist, Bilder/Videos hinzufügen.

<u>Zu reproduzierende Schritte</u>

1. Melden Sie sich als Administrator an.
1. Erstellen Sie eine zweite Website-, Store- und Store-Ansicht.
1. Erstellen Sie eine zweite Administratorrolle mit Ressourcen, die nur für die zweite Website-, Store- und Store-Ansicht verwendet werden.
1. Erstellen Sie einen zweiten Administrator und weisen Sie ihn der neuen eingeschränkten Administratorrolle zu.
1. Erstellen Sie ein neues Produkt und weisen Sie es sowohl den standardmäßigen als auch den neuen Websites zu.
1. Melden Sie sich vom Hauptadministrator ab.
1. Melden Sie sich als neuer eingeschränkter Administrator an.
1. Bearbeiten Sie das erstellte Produkt, das beiden Websites zugewiesen wurde.
1. Öffnen Sie die **[!UICONTROL Images and Videos]** Registerkarte.

<u>Erwartete Ergebnisse</u>:

* Die folgende Meldung wird angezeigt:

  *Der eingeschränkte Administrator darf nur dann Aktionen mit Bildern oder Videos durchführen, wenn der Administrator über Berechtigungen für alle Websites verfügt, denen das Produkt zugewiesen ist.*

* Die **[!UICONTROL Add Video]** -Schaltfläche nicht aktiv ist.

<u>Tatsächliche Ergebnisse</u>:

Der eingeschränkte Administrator kann Bilder und Videos hinzufügen, selbst wenn das Produkt einer Website zugewiesen ist, auf die er keinen Zugriff hat.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
