---
title: Überprüfen Sie den Patch auf Adobe Commerce-Problem mit dem Tool für Qualitätsmuster .
description: Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die erklären, wie es verwendet wird.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Überprüfen Sie den Patch auf Adobe Commerce-Problem mit dem Tool für Qualitätsmuster .

Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die erklären, wie es verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort, alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Qualitätsmuster-Werkzeug

Die [Werkzeug für Qualitätsmuster](https://github.com/magento/quality-patches) (QPT) sind individuelle Patches, die von Adobe und der Magento Open Source Community entwickelt werden.

Damit können Sie:

* Anwendung von Qualitätspatches, die im Paket enthalten sind
* Zurücksetzen zuvor angewendeter Patches
* Hier finden Sie allgemeine Informationen zu Qualitätspatches, die für die installierte Version von Adobe Commerce verfügbar sind.

Im Folgenden finden Sie ein Beispiel für die Statustabelle, die Sie aufrufen können, um die verfügbaren Patches anzuzeigen:

![Magento_patches_list](assets/status_table.png)

Das Tool soll Ihnen die Möglichkeit geben, Patches für Probleme, die mit Adobe Commerce auftreten können, selbst zu bedienen oder einfach durch den Adobe Commerce-Support vorgeschlagene Patches anzuwenden.

>[!NOTE]
>
>QPT ist nur für Qualitäts-Patches geeignet. Sicherheitspatches sind im Abschnitt [Magento Security Center](https://magento.com/security/patches).

## Im Werkzeug für Qualitätsmuster verfügbare Patches

Siehe [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation für die Liste der verfügbaren Patches.

## Installieren und Verwenden des Tools &quot;Qualitätsmuster&quot;

Die Installations- und Nutzungsbefehle unterscheiden sich für Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur, da für Cloud das QPT-Paket im ece-Tools-Paket enthalten ist.

### Installation und Verwendung von QPT für Adobe Commerce vor Ort

Siehe [Handbuch für Software-Updates > Patchen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation für Informationen zur Installation und Verwendung von QPT zum Anwenden und Zurücksetzen von Patches.

### Installieren und Verwenden von QPT für Adobe Commerce in der Cloud-Infrastruktur

Siehe [Cloud für Adobe Commerce > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation für Informationen zur Installation und Verwendung von QPT für die Anwendung und Wiederherstellung von Patches auf Adobe Commerce in der Cloud-Infrastruktur.

## Verwandtes Lesen

* [Versionshinweise zum Qualitätsmuster-Tool](https://devdocs.magento.com/quality-patches/release-notes.html) in unserer Entwicklerdokumentation.
* [Anwenden von Composer-Patches, die von Adobe bereitgestellt werden](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Wissensdatenbank.
