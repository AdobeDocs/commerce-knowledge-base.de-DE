---
title: 'ACSD-42807: Benutzerdefiniertes Währungszeichen wird nicht auf der Storefront angezeigt'
description: Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-42807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: Benutzerdefiniertes Währungszeichen wird nicht auf der Storefront angezeigt

Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-42807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das benutzerdefinierte Währungszeichen wird nicht auf der Storefront angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Währungseinstellungen** und wählen Sie eine beliebige benutzerdefinierte Währung aus. Beispiel: **Mexikanischer Peso**.
1. Wechseln Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Gebietsschemaoptionen** und wählen Sie **Spanisch (Mexiko)** aus.
1. Wechseln Sie zu **Store** > **Währungssymbole** und konfigurieren Sie das Währungssymbol in **MX$**.
1. Überprüfen Sie das Währungssymbol auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Das Standardwährungssymbol lautet &quot;MX$&quot;, wobei die Währung auf &quot;Mexikanischer Peso&quot;und das Gebietsschema auf &quot;Spanisch (Mexiko)&quot;eingestellt ist.

<u>Tatsächliche Ergebnisse</u>:

Das Standardwährungssymbol zeigt &quot;$&quot;.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
