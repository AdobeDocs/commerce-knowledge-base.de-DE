---
title: '''MDVA-41215: Benutzer erhalten 500 Fehler nach dem Setzen des Cookies "mage-messages".'
description: Der Patch MDVA-41215 behebt das Problem, dass Benutzer nach dem Setzen des Cookies "Bildnachrichten"einen 500-Fehler erhalten, wenn er bereits vorhanden ist, aber keine neuen Nachrichten vorhanden sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-41215. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 93555984-1eed-4866-ab49-5467f9afd124
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# MDVA-41215: Benutzer erhalten 500 Fehler nach dem Setzen des Cookies &quot;mage-messages&quot;.

Der Patch MDVA-41215 behebt das Problem, dass Benutzer nach dem Setzen des Cookies &quot;Bildnachrichten&quot;einen 500-Fehler erhalten, wenn er bereits vorhanden ist, aber keine neuen Nachrichten vorhanden sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-41215. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten 500 Fehler, nachdem sie das Cookie &quot;Bildnachrichten&quot;gesetzt haben, sofern es bereits vorhanden ist, aber keine neuen Nachrichten vorhanden sind.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu &quot;**../customer/account/login**&quot;.
1. Öffnen Sie die Registerkarte &quot;Netzwerk&quot;in den Entwicklungs-Tools des Browsers (stellen Sie sicher, dass das Protokoll beibehalten aktiviert ist).
1. Füllen Sie das Formular mit ungültigen Werten aus (Anmeldung sollte fehlschlagen).
1. Klicken Sie auf **Senden**.
1. Kopieren Sie als cURL die erste Anforderung auf der Registerkarte &quot;Netzwerk&quot;und suchen Sie nach den Werten &quot;PHPSESSID&quot;und &quot;form_key&quot;.
1. Ersetzen Sie PHPSESSID- und form_key-Werte in der aktualisierten cURL-Anforderung und senden Sie sie.

```curl -sSL -D - 'http://magento24.loc/customer/account/loginPost/' -i -o /dev/null \
--data-raw 'form_key=i4UVctCCEdAlG13P&login%5Busername%5D=aaa%40bbb.ccc&login%5Bpassword%5D=qwerty' \
--header 'cookie: mage-messages=%5B%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%5D; PHPSESSID=l5575pntrhopuk3ld6maf5aa2m; mage-messages=%5B%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%5D; private_content_version=0de5bf3a3e27e966dd5d6c1ee84e27a7'
```

<u>Erwartete Ergebnisse</u>:

Benutzer erhalten `HTTP/1.1 200 OK`

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten `HTTP/1.1 500 Internal Server Error`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
