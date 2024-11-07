---
title: "MDVA-38827: Kunden erhalten einen Auftragsversandfehler per E-Mail."
description: "Der Patch MDVA-38827 behebt das Problem, dass Kunden eine E-Mail zum Bestellversand mit der folgenden Fehlermeldung erhalten: *Es tut uns leid, dass bei der Generierung dieses Inhalts ein Fehler aufgetreten ist*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll."
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Kunden erhalten per E-Mail einen Auftragsversandfehler

Der Patch MDVA-38827 behebt das Problem, bei dem Kunden eine E-Mail zum Bestellversand mit der folgenden Fehlermeldung erhalten: *Es tut uns leid, es ist ein Fehler beim Generieren dieses Inhalts aufgetreten*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn die Option Kunden per E-Mail benachrichtigen für den Versand ausgewählt ist, erhalten Kunden eine E-Mail mit der folgenden Fehlermeldung: *Es tut uns leid, es ist ein Fehler beim Generieren dieses Inhalts aufgetreten*.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Marketing** > **Kommunikation** > **E-Mail-Vorlagen** und wählen Sie **Neue Vorlage hinzufügen** aus.
   * Wählen Sie **Magento Sales** > **New Shipping**.
   * Klicken Sie auf **Vorlage laden**.
   * Fügen Sie einen Vorlagennamen hinzu (z. B. die Kernversandvorlage) und klicken Sie auf **Speichern**.
1. Wechseln Sie zu **Store** > Einstellungen > **Konfiguration** > **Verkauf** > **E-Mail-Vertrieb**:
   * Aktivieren Sie **Versandkommentare**.
   * Wählen Sie unter &quot;E-Mail-Vorlage für Versandkommentar&quot;und &quot;E-Mail-Vorlage für Versandkommentar&quot;die Option **Kernversandvorlage** (siehe Schritt 1 &quot;Vorlagennamen hinzufügen&quot;).
1. Bestellung aufgeben. Gehen Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellung**, klicken Sie auf **Ansicht** und senden Sie dann die Bestellung.
1. Der Bestellstatus ändert sich von &quot;Ausstehend&quot;zu &quot;Verarbeitung&quot;.
1. Klicken Sie im linken Seitenleistenmenü auf **Sendungen** und dann auf **Ansicht** , um die Reihenfolge anzuzeigen.
1. Fügen Sie einen Kommentar im Text **Kommentar** unter **Versandverlauf** hinzu und aktivieren Sie das Kontrollkästchen **Kunden per E-Mail benachrichtigen** .
1. Klicken Sie auf **Kommentar senden**.

<u>Erwartete Ergebnisse</u>:

Es wird eine Verkaufs-E-Mail mit Versandkommentaren erzeugt.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird in der E-Mail empfangen: *Es tut uns leid, dass bei der Erstellung dieses Inhalts ein Fehler aufgetreten ist.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
