---
title: 'MDVA-32739 Patch: Alte E-Mails, die beim Aktivierung des asynchronen Versands gesendet werden'
description: Der Patch MDVA-32739 behebt das Problem, dass bei der Aktivierung von [asynchronen E-Mail-Benachrichtigungen](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) alte Verkaufs-E-Mails gesendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben sein soll.
exl-id: 8cf4ef8a-f2f2-47fb-9f69-0eedcc10ba8b
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Patch MDVA-32739: alte E-Mails, die gesendet werden, wenn der asynchrone Versand aktiviert ist

Der Patch MDVA-32739 behebt das Problem, bei dem die Aktivierung von [Asynchrone E-Mail-Benachrichtigungen](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) sendet alte Verkaufs-E-Mails. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Deaktivieren Sie den asynchronen E-Mail-Versand.
1. Erstellen Sie eine Bestellung und stellen Sie sicher, dass der Versand der E-Mail fehlschlägt.
1. Aktivieren Sie das asynchrone Senden.

<u>Erwartete Ergebnisse</u>:

E-Mails werden nur für Bestellungen, Sendungen, Rechnungen und Kreditkarten gesendet, die nach der letzten Aktualisierung des asynchronen Versands erstellt wurden.

<u>Tatsächliche Ergebnisse</u>:

Die alte E-Mail wird über den Cronjob gesendet.

## Fehlerbehebung

Mit der im Patch enthaltenen Fehlerbehebung wählt Adobe Commerce Bestellungen aus, die nach der letzten Ausführung der asynchronen Versandmethode erstellt wurden, und sendet die E-Mail für solche Bestellungen.

Standardmäßig wird sie mit einem Versatz von -1 Tag ausgewählt.

Sie können diesen Wert ändern (z. B. auf -2 Tage), indem Sie `di.xml`.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
