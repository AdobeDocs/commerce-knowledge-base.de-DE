---
title: Tipps zum Testen von Drittanbietern für Adobe Commerce in der Cloud-Infrastruktur
description: Dieser Artikel bietet Optionen zum Freigeben des Zugriffs für einen Drittanbieter für Tests/Validierungen, wenn Sie ein Problem mit einer Erweiterung für Adobe Commerce in der Cloud-Infrastruktur haben.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Tipps zum Testen von Drittanbietern für Adobe Commerce in der Cloud-Infrastruktur

Dieser Artikel bietet Optionen zum Freigeben des Zugriffs für einen Drittanbieter für Tests/Validierungen, wenn Sie ein Problem mit einer Erweiterung für Adobe Commerce in der Cloud-Infrastruktur haben.
Bei der Entscheidung, wie der Zugang zu einem Dritten ermöglicht werden soll, sollten Sie die entsprechenden internen Datensicherheitsverfahren und -anforderungen befolgen.

## Betroffene Produkte und Versionen:

* Adobe Commerce für Cloud-Infrastruktur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Welche Umgebungen zum Testen zu verwenden sind

Abhängig von Ihren internen Sicherheitsstandards können Sie die Fehlerbehebung bei Drittanbietern in einer lokalen Umgebung durchführen. Wenn das Problem nicht lokal reproduziert werden kann, sollten Sie Zugriff auf Ihre Cloud-Umgebung gewähren. Wenn Sie dies tun möchten, stellen Sie bitte sicher, dass Sie innerhalb Ihrer internen Sicherheitsstandards arbeiten. Stellen Sie bei der Bereitstellung des Zugriffs auf eine Ihrer Cloud-Umgebungen sicher, dass Ihr Drittanbieter genau weiß, was getan werden kann und welche Genehmigung für Dinge wie Replikation nur erforderlich ist oder Codeänderungen möglich sind. Dies ist besonders für Produktionsumgebungen wichtig.

## Zugriff auf und Daten von Drittanbietern

* Gewähren Sie Ihrem Drittanbieter Zugriff auf die Cloud-Umgebung. Verwandte Artikel:

   * [Adobe Commerce Help Center-Benutzerhandbuch > FREIGEGEBENER ZUGRIFF: GEWÄHREN SIE ANDEREN BENUTZERN BERECHTIGUNGEN FÜR DEN ZUGRIFF AUF IHR KONTO](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) IN unserer Support-Wissensdatenbank.
   * [Freigeben Ihres Commerce-Kontos](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-share) in unserem Benutzerhandbuch.

* Erstellen Sie eine Datenbank-Ablage (oder gewähren Sie dem Drittanbieter Zugriff darauf). Dies kann über die CLI oder im Commerce Admin erfolgen. Dieser DB-Dump verschleiert Kundendaten, sodass sie nur Code- und Produkt-SKUs usw. erhalten, keine proprietären/Kundendaten. Verwenden Sie als Referenz [Freigeben Ihres Commerce-Kontos] (/help/how-to/general/create-database-dump-on-cloud.md) in unserer Support-Wissensdatenbank.
* Stellen Sie nach Abschluss des Tests sicher, dass Sie den freigegebenen Zugriff auf Ihre Cloud-Umgebung widerrufen, wie unter [Benutzerhandbuch für das Adobe Commerce Help Center > Sperren (freigegebenen Zugriff löschen)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) in unserer Support-Wissensdatenbank beschrieben.

## Best Practice testen

Es wird üblich, eine Fehlerbehebung in einer lokalen Umgebung durchzuführen. Wenn das Problem nicht lokal reproduziert werden kann, gehen Sie zu Staging. Möglicherweise muss der Drittanbieter die Produktion überprüfen. Stellen Sie sicher, dass Ihr Drittanbieter weiß, dass er nur versuchen soll, das Problem in Produktion und Staging zu reproduzieren und keine Code-Änderungen vorzunehmen. Wenn er Codeänderungen vornehmen muss, muss er zunächst Ihre Berechtigung erhalten.

## Verwandtes Lesen

* [Best Practices für die Verwendung von Erweiterungen von Drittanbietern in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) in unserer Support-Wissensdatenbank.
