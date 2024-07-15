---
title: "MDVA-12304: 503-Fehler bei Storefront und Cookie-Fehler"
description: Dieser MDVA-12304 Adobe Commerce-Patch löst 503 Fehler an Store-Fronten, wobei *das Cookie nicht senden kann. Die maximale Anzahl von Cookies würde überschritten.* Fehlermeldung in Protokollen. Dies ist ein bekanntes Problem mit Adobe Commerce 2.2.5. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304: 503-Fehler bei Storefront und Cookie-Fehler

Dieser MDVA-12304 Adobe Commerce-Patch behebt 503 Fehler an Store-Fronten, wobei *das Cookie nicht senden kann. Die maximale Anzahl von Cookies würde überschritten.* Fehlermeldung in Protokollen. Dies ist ein bekanntes Problem mit Adobe Commerce 2.2.5. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist.

## Betroffene Produkte und Versionen

* **Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce lokal 2.2.5.
* **Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce (alle Bereitstellungsmethoden) 2.x.x.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kunden erhalten beim Navigieren in der Storefront einen 503-Fehler. In der Datei `var/log/exception.log` gibt es die folgende Fehlermeldung *Cookie kann nicht gesendet werden. Die maximale Anzahl von Cookies würde überschritten.*

Das Problem tritt auf, weil die standardmäßige Cookie-Grenze von Adobe Commerce auf 50 festgelegt ist. Wenn der Browser des Kunden die Beschränkung erreicht, löst Commerce eine Ausnahme aus. Die im Patch bereitgestellte Lösung erhöht das Cookie-Limit auf 200.

<u>Zu reproduzierende Schritte:</u>

Der 503-Fehler kann jederzeit angezeigt werden, wenn der Kunde versucht, sich anzumelden und seinen Warenkorb anzuzeigen.

In der Datei `var/log/exception.log` gibt es die folgende Fehlermeldung *Cookie kann nicht gesendet werden. Die maximale Anzahl von Cookies würde überschritten.*

<u>Tatsächliches Ergebnis:</u> Der Kunde kann seinen Warenkorb nicht überprüfen oder seine Bestellung abschließen.

<u>Erwartetes Ergebnis:</u> Der Kunde kann seinen Warenkorb überprüfen und seine Bestellung abschließen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.


## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
