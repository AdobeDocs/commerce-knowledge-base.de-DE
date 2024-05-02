---
title: "ACSD-46404: Admin-Benutzer können sich nach einem Upgrade auf 2.4.4 nicht anmelden."
description: Der Patch ACSD-46404 behebt das Problem, dass sich ein Admin-Benutzer nach einem Upgrade auf 2.4.4 nicht anmelden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 installiert ist. Die Patch-ID ist ACSD-46404. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.
exl-id: 0aebc879-1128-4be2-a6a8-90d5812c7602
feature: Admin Workspace
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-46404: Admin-Benutzer können sich nach einem Upgrade auf 2.4.4 nicht mehr anmelden

Der Patch ACSD-46404 behebt das Problem, dass sich ein Admin-Benutzer nach einem Upgrade auf 2.4.4 nicht anmelden kann. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) Version 1.1.19 ist installiert. Die Patch-ID ist ACSD-46404. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator kann sich nach einem Upgrade auf 2.4.4 nicht mehr anmelden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin Panel an
1. Navigieren Sie zu Store > **Einstellungen** > **Konfiguration** > **Erweitert** > **System** > **Sicherheit**.
1. Setzen Sie die maximale Sitzungsgröße in Admin auf . **0** und speichern Sie es.

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer kann sich erfolgreich anmelden.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator wird abgemeldet und kann sich nicht anmelden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
