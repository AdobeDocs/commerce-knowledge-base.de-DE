---
title: Patch auf Adobe Commerce-Probleme mit dem Quality Patches Tool überprüfen
description: Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die seine Verwendung erklären.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: ce9c69e12d64b4b4a8e6129783d9b15e95eff867
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Patch auf Adobe Commerce-Probleme mit dem Quality Patches Tool überprüfen

Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die seine Verwendung erklären.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Was sind Quality Patches Tool?

Das [Quality Patches Tool](https://github.com/magento/quality-patches) (QPT) sind individuelle Patches, die von Adobe und der Magento Open Source-Community entwickelt wurden.

Damit können Sie:

* Anwenden von Qualitäts-Patches, die im Paket enthalten sind
* Zuvor angewendete Patches wiederherstellen
* Sehen Sie sich die allgemeinen Informationen über Qualitäts-Patches an, die für die installierte Version von Adobe Commerce verfügbar sind.

Im Folgenden finden Sie ein Beispiel für die Statustabelle, die Sie erhalten können, um die verfügbaren Patches anzuzeigen:

![Magento_PATCHES_LIST](assets/status_table.png)

Das Tool soll Ihnen die Möglichkeit geben, selbst Patches für Probleme zu erstellen, die möglicherweise bei Adobe Commerce auftreten, oder einfach Patches anzuwenden, die vom Adobe Commerce-Support vorgeschlagen werden.

>[!NOTE]
>
>QPT ist nur für qualitativ hochwertige Patches. Sicherheits-Patches sind im [Magento-Sicherheitscenter](https://magento.com/security/patches) verfügbar.

## Im Quality Patches Tool verfügbare Patches

Eine Liste der verfügbaren Patches finden Sie [Quality Patches Tool](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.

## Installieren und Verwenden des Quality Patches Tools

Die Installations- und Verwendungsbefehle für Adobe Commerce On-Premise und Adobe Commerce On Cloud Infrastructure unterscheiden sich, da das QPT-Cloud-Paket im Paket ece-tools enthalten ist.

### Installieren und Verwenden von QPT für Adobe Commerce On-Premise

Weitere Informationen [ Installation und Verwendung von QPT zum Anwenden und Zurücksetzen von Patches finden Sie unter ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)Software-Update-Handbuch > Patching“ in unserer Entwicklerdokumentation.

### Installieren und Verwenden von QPT für Adobe Commerce in der Cloud-Infrastruktur

Weitere Informationen zur Installation und Verwendung von QPT zum Anwenden und Zurücksetzen von Patches auf [ Cloud-Infrastruktur finden Sie unter „Cloud ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) für Adobe Commerce Adobe Commerce > Patches anwenden in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Versionshinweise zum Quality Patches Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) in unserer Entwicklerdokumentation.
* [Anwenden von Composer-Patches von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank.

