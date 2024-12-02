---
title: 'MDVA-38799: Herunterladbare Produkte, die nach der Erstellung eines Staging-Updates nicht gespeichert wurden'
description: Der Patch MDVA-38799 behebt das Problem, dass herunterladbare Produkte nach der Erstellung eines Staging-Updates nicht gespeichert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38799. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799: Herunterladbare Produkte, die nach der Erstellung eines Staging-Updates nicht gespeichert wurden

Der Patch MDVA-38799 behebt das Problem, dass herunterladbare Produkte nach der Erstellung eines Staging-Updates nicht gespeichert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38799. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Herunterladbare Produkte werden nach dem Erstellen eines Staging-Updates nicht gespeichert. Benutzer erhalten die Fehlermeldung: *Das herunterladbare Beispiel ist nicht mit dem Produkt verknüpft. Überprüfen Sie den Link und versuchen Sie es erneut*.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Katalog** > **Produkte**.
1. Klicken Sie auf das Dropdown-Menü neben Produkt hinzufügen und wählen Sie Herunterladbares Produkt aus.
   * Geben Sie den Namen, die SKU, den Preis und die Menge des Produkts an.
1. Scrollen Sie nach unten zur Seite &quot;Download-Informationen&quot;.
1. Klicken Sie unter &quot;Beispiele&quot;auf **Link hinzufügen**.
   * Füllen Sie den Titel und die Upload-Datei aus (der Dateityp spielt keine Rolle).
1. Klicken Sie auf **Speichern**. Sie erhalten die folgende Meldung: *Sie haben das Produkt gespeichert*.
1. Klicken Sie oben auf der Seite auf **Neues Update planen** .
   * Geben Sie den Aktualisierungsnamen sowie ein gültiges Start- und Enddatum ein.
1. Klicken Sie beim Staging-Update auf **Speichern** .
1. Klicken Sie auf **Speichern** für das Produkt.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird ohne Fehler gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die Fehlermeldung: *Das herunterladbare Beispiel ist nicht mit dem Produkt verknüpft. Überprüfen Sie den Link und versuchen Sie es erneut*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
