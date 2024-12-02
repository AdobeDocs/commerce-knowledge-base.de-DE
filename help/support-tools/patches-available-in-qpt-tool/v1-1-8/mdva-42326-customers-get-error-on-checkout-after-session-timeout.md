---
title: 'MDVA-42326: Kunden erhalten beim Checkout nach Sitzungs-Timeout einen Fehler'
description: Der Patch MDVA-42326 behebt das Problem, dass Kunden nach dem Sitzungs-Timeout beim Checkout einen Fehler beim Checkout erhalten, selbst wenn der beständige Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Kunden erhalten beim Checkout nach Sitzungs-Timeout einen Fehler

Der Patch MDVA-42326 behebt das Problem, dass Kunden nach dem Sitzungs-Timeout beim Checkout einen Fehler beim Checkout erhalten, selbst wenn der beständige Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kunden erhalten nach dem Sitzungs-Timeout beim Checkout einen Fehler, selbst wenn der beständige Warenkorb aktiviert ist.

<u>Voraussetzungen</u>:

1. Wechseln Sie zu **Konfiguration** > **Allgemein** > **Web** > **Standard-Cookie-Einstellungen** > **Cookie-Lebensdauer** und legen Sie den Wert auf **120** fest.
1. Wechseln Sie zu **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Online-Kundenoptionen** und legen Sie beide Werte auf **2** fest.
1. Wechseln Sie zu **Konfiguration** > **Kunden** > **Warenkorb für beständige Käufe** und legen Sie **Aktivieren** fest.
1. Wechseln Sie zu **Konfiguration** > **Verkauf** > **Zahlungsmethoden** und deaktivieren Sie alle Zahlungsmethoden mit Ausnahme von **Bestellung prüfen/bestellen** (es sollte aktiviert sein).

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Kunde an und fügen Sie einige Produkte zum Warenkorb hinzu.
1. Überprüfen Sie den Warenkorb.
1. Warten Sie zwei Minuten (in Vorbedingung gesetzt); die Sitzung sollte mit einem Timeout beendet werden.
1. Klicken Sie auf **Zum Checkout wechseln** und aktualisieren Sie die Seite nicht.
1. Checkout als Gast, füllen Sie die Lieferadresse aus und wählen Sie eine Versandmethode.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie auf der Seite **Überprüfen und Zahlungen** auf **Bestellung platzieren**. Da nur eine Zahlungsmethode zulässig ist, sollte der Kunde die Bestellung aufgeben können, ohne die Zahlungsmethode auszuwählen.

<u>Erwartete Ergebnisse</u>:

Der Kunde sollte die Bestellung aufgeben können.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält den folgenden Fehler: *Validierung der fehlgeschlagenen Adresse: E-Mail hat ein falsches Format*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
