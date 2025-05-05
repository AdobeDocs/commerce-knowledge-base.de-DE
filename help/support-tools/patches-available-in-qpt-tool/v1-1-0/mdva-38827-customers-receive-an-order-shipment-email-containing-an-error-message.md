---
title: 'MDVA-38827: Kunden erhalten Bestellversandfehler per E-Mail'
description: 'Mit dem Patch MDVA-38827 wird das Problem behoben, dass Kunden eine E-Mail mit einer Bestellsendung erhalten, die die folgende Fehlermeldung enthält: *Es tut uns leid, bei der Erstellung dieses Inhalts ist ein Fehler aufgetreten*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.'
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Kunden erhalten Bestellversandfehler per E-Mail

Der Patch MDVA-38827 behebt das Problem, dass Kunden eine E-Mail mit einer Bestellsendung erhalten, die die folgende Fehlermeldung enthält: *Es tut uns leid, bei der Erstellung dieses Inhalts ist ein Fehler aufgetreten*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn die Option Kunden per E-Mail benachrichtigen für den Versand ausgewählt ist, erhalten Kunden eine E-Mail mit der folgenden Fehlermeldung: *Beim Generieren dieses Inhalts ist ein Fehler aufgetreten*.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **Marketing** > **Kommunikation** > **E-Mail-** und wählen Sie **Neue Vorlage hinzufügen**.
   * Wählen Sie **Magento Vertrieb** > **Neue Lieferung**.
   * Klicken Sie auf **Vorlage**.
   * Fügen Sie einen Vorlagennamen hinzu (z. B. „Core-Versandvorlage„) und klicken Sie auf **Speichern**.
1. Wechseln Sie zu **Store** > Einstellungen > **Konfiguration** > **Verkauf** > **Verkaufs-E-Mail**:
   * Aktivieren Sie **Versandkommentare**.
   * Wählen Sie **Core-Versandvorlage** (siehe den Teil „Vorlagennamen hinzufügen“ in Schritt 1) unter E-Mail-Vorlage für Versandkommentare und E-Mail-Vorlage für Versandkommentare für Gäste aus.
1. Bestellung aufgeben. Gehen Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellung**, klicken Sie auf **Anzeigen** und versenden Sie dann die Bestellung.
1. Der Bestellstatus ändert sich von „Ausstehend“ in „Verarbeitung läuft“.
1. Klicken Sie **linken Seitenleiste auf** Sendungen“ und dann auf **Anzeigen**, um die Bestellung anzuzeigen.
1. Fügen Sie in **Kommentartext** unter **Versandverlauf** einen Kommentar ein und aktivieren Sie das Kontrollkästchen **Kunden per E-Mail benachrichtigen**.
1. Klicken Sie **Kommentar übermitteln**.

<u>Erwartete Ergebnisse</u>:

Verkaufs-E-Mail mit Versandkommentaren wird generiert.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird in der E-Mail empfangen: *Beim Generieren dieses Inhalts ist ein Fehler aufgetreten.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
