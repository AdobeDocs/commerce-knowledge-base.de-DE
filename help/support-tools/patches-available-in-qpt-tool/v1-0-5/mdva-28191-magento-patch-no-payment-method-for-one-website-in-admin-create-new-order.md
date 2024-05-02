---
title: "MDVA-28191: Keine Zahlungsmethode für eine Website in Admin Create New Order"
description: Der Patch MDVA-28191 behebt das Problem, dass eine Zahlungsmethode nicht in den Admin geladen wird, **Neue Bestellung erstellen** für eine Website, obwohl Zahlungsmethoden für andere Websites angezeigt werden können.  Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) Tool Version 1.0.5 installiert ist.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191: Keine Zahlungsmethode für eine Website in Admin Neue Bestellung erstellen

Der Patch MDVA-28191 behebt das Problem, dass eine Zahlungsmethode im Admin nicht geladen wird **Neue Bestellung erstellen** für eine Website, obwohl Zahlungsmethoden für andere Websites angezeigt werden können.  Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) -Tool-Version 1.0.5 installiert ist.

## Betroffene Produkte und Versionen

Adobe Commerce lokal und Adobe Commerce auf Cloud-Infrastruktur 2.3.3 bis 2.4.1 (einschließlich 2.3.5-p1).

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Erstellen einer Bestellung aus dem Backend erstellt Adobe Commerce zwei Anführungszeichen: eine ist inaktiv und die andere aktiv. Die Sitzung enthält jedoch die inaktive Anführungszeichen-ID.

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zu **Admin Panel** > **Vertrieb** > **Bestellungen** und klicken Sie auf **Neue Bestellung erstellen** Schaltfläche.
1. Wählen Sie den Kunden aus, für den Sie die Bestellung erstellen möchten.
1. Wenn Ihr Store mehrere Ansichten hat, wählen Sie die Store-Ansicht, in der die Bestellung platziert werden soll, auf der **Neue Bestellung erstellen** Seite für den ausgewählten Benutzer.
1. Fügen Sie Produkte aus der **Kundenaktivitäten** oder aus dem Katalog durch Klicken auf **Produkte hinzufügen**. Scrollen Sie nach unten auf der Seite, um die folgenden Abschnitte für die Bestellung abzuschließen:
   * Coupon-Codes anwenden
   * Zahlungsmethode
   * Versandmethode
   * Bestellkommentare

<u>Erwartetes Ergebnis:</u>

Zahlungsmethoden sollten für alle Websites in den Admin geladen werden.

<u>Ergebnis:</u>

Keine Zahlungsmethode verfügbar (auch keine Nachricht &quot;*Keine Zahlungsinformationen erforderlich*&quot; angezeigt) für diese Website, obwohl Zahlungsmethoden beim Testen von Bestellungen für andere Websites angezeigt werden können.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
