---
title: "Patch MDVA-30593: abgelaufene Anführungszeichen werden nicht bereinigt"
description: Der Patch MDVA-30593 behebt das Problem, bei dem Anführungszeichen, die gemäß der Einstellung **Anführungszeitraum** abgelaufen sind, nicht bereinigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.4 behoben wurde.
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Patch MDVA-30593: abgelaufene Anführungszeichen werden nicht bereinigt

Der Patch MDVA-30593 behebt das Problem, bei dem Zitate, die gemäß der **Anführungszeiten** nicht bereinigt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.3.4 behoben wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.3.3.x

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Anführungszeichen, die gemäß **Anführungszeiten** nicht bereinigt werden.

<u>Zu reproduzierende Schritte:</u>

1. Navigieren Sie im Commerce-Admin zu **Stores** > **Konfiguration** > **Vertrieb** > **Checkout** > **Warenkorb**.
1. Satz **Anführungszeitraum (Tage)** = *1*
1. Speichern Sie die Konfiguration und leeren Sie den Cache.
1. Melden Sie sich als Kunde an.
1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Gehen Sie nach einem Tag wieder in den Warenkorb.

<u>Erwartetes Ergebnis:</u>

Das Angebot wird gelöscht und das Produkt wird aus dem Warenkorb entfernt, da der alte Preis nicht mehr gültig ist.

<u>Ergebnis:</u>

Das Produkt befindet sich noch im Warenkorb.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
