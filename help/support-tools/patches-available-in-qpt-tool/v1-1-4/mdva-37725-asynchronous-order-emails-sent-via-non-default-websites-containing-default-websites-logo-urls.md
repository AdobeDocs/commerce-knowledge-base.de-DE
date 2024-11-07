---
title: "MDVA-37725: E-Mails, die über nicht standardmäßige Websites gesendet werden, enthalten die Standard-Logo-URLs der Site."
description: Der Patch MDVA-37725 behebt das Problem, dass asynchrone E-Mails über nicht standardmäßige Websites mit Logo-URLs von der Standardwebsite gesendet werden.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725: E-Mails, die über nicht standardmäßige Websites gesendet werden, enthalten die Standard-Logo-URLs der Site

>[!WARNING]
>
> Das MDVA-37725-Patch wird nicht mehr unterstützt.

Der Patch MDVA-37725 behebt das Problem, dass asynchrone E-Mails über nicht standardmäßige Websites mit Logo-URLs von der Standardwebsite gesendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-37725. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

E-Mails asynchroner Bestellungen werden über nicht standardmäßige Websites mit den Logo-URLs der Standardwebsite gesendet.

<u>Voraussetzungen</u>:

1. Die zweite Website-/Store-/Store-Ansicht muss erstellt worden sein.
1. Die Konfiguration **Asynchrones Senden** muss unter **Stores** > **Einstellungen** > **Konfiguration** > **Vertrieb** > **E-Mail-Vertrieb** > **Allgemeine Einstellungen** aktiviert werden.
1. Die Konfiguration **Speichercode zu URLs hinzufügen** ist aktiviert, damit Sie problemlos von **Stores** > **Einstellungen** > **Konfiguration** > **URL-Optionen** auf die sekundäre Website zugreifen können.

<u>Zu reproduzierende Schritte</u>:

1. Bestellen Sie Bestellungen sowohl aus dem ersten als auch aus dem zweiten Geschäft.
1. Führen Sie cron aus, um die Verkaufs-E-Mails zu senden.
1. Prüfen Sie die E-Mail von der zweiten Website.

<u>Erwartete Ergebnisse</u>:

Die Logo-URL der E-Mail enthält die URL der zweiten Website.

<u>Tatsächliche Ergebnisse</u>:

Die Logo-URL der E-Mail enthält die Standard-URL der Website.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
