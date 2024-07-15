---
title: "MDVA-30265: Tracking-Link in E-Mail gibt 404 Seite nicht gefunden zurück"
description: Der Patch MDVA-30265 löst das Problem des Fehlers "404 Seite nicht gefunden", wenn der Kunde auf den Versand-Tracking-Link in der Auftragsbestätigungs-E-Mail klickt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265: Tracking-Link in E-Mail gibt 404 Seite nicht gefunden zurück

Der Patch MDVA-30265 löst das Problem des Fehlers &quot;404 Seite nicht gefunden&quot;, wenn der Kunde auf den Versand-Tracking-Link in der Auftragsbestätigungs-E-Mail klickt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 bis 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nachdem der Versand für eine Bestellung erstellt wurde, wird eine E-Mail mit Tracking-Informationen und einem Link zur Nachverfolgung der Bestellung an den Kunden gesendet. Wenn der Kunde jedoch auf den Link zum Versand-Tracking in der E-Mail klickt, wird der Fehler &quot;404 Seite nicht gefunden&quot;zurückgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce 2.4. Anweisungen finden Sie unter [Installieren von Adobe Commerce mithilfe von Composer](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) in unserer Entwicklerdokumentation.
1. Bestellung aufgeben.
1. Gehen Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellungen**. Suchen Sie nach der soeben erstellten Bestellung und öffnen Sie sie.
1. Erstellen Sie eine Sendung und fügen Sie eine Trackingnummer hinzu (Carrier = Benutzerdefinierter Wert). Anweisungen hierzu finden Sie in unserem Benutzerhandbuch unter [Order Management > Erstellen einer Sendung](https://docs.magento.com/user-guide/sales/shipments-create.html) .
1. Sie erhalten eine E-Mail. Klicken Sie auf den Trackinglink, um zu überprüfen, ob er funktioniert.
1. Erstellen Sie eine Rechnung. Anweisungen hierzu finden Sie in unserem Benutzerhandbuch unter [Order Management > Rechnungserstellung](https://docs.magento.com/user-guide/sales/invoice-create.html) . Klicken Sie dann erneut auf den obigen Tracking-Link.

<u>Erwartete Ergebnisse</u>:

Der Tracking-Link sollte auch nach der Erstellung der Rechnung funktionieren.

<u>Tatsächliche Ergebnisse</u>:

Nach der Erstellung der Rechnung funktioniert der Tracking-Link nicht und gibt die Fehlerseite &quot;404 Seite nicht gefunden&quot;zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
