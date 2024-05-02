---
title: "ACSD-42807: Benutzerdefiniertes Währungszeichen nicht auf Storefront angezeigt"
description: Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-42807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: Benutzerdefiniertes Währungszeichen wird nicht auf der Storefront angezeigt

Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-42807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das benutzerdefinierte Währungszeichen wird nicht auf der Storefront angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Währungseinstellungen** und wählen Sie eine benutzerdefinierte Währung aus. Beispiel: **Mexiko, Peso**.
1. Navigieren Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Gebietsschemaoptionen** und wählen **Spanisch (Mexiko)**.
1. Navigieren Sie zu **Store** > **Währungssymbole** und konfigurieren Sie das Währungssymbol in **MX$**.
1. Überprüfen Sie das Währungssymbol auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Das Standardwährungssymbol lautet &quot;MX$&quot;, wobei die Währung auf &quot;Mexikanischer Peso&quot;und das Gebietsschema auf &quot;Spanisch (Mexiko)&quot;eingestellt ist.

<u>Tatsächliche Ergebnisse</u>:

Das Standardwährungssymbol zeigt &quot;$&quot;.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
