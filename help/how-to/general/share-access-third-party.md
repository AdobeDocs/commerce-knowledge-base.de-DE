---
title: Tipps von Drittanbietern zum Testen von Adobe Commerce in Cloud-Infrastrukturen
description: Dieser Artikel bietet Optionen zum Freigeben des Zugriffs für einen Drittanbieter zum Testen/Validieren, wenn Sie ein Problem mit einer Erweiterung für Adobe Commerce in der Cloud-Infrastruktur haben.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Tipps von Drittanbietern zum Testen von Adobe Commerce in Cloud-Infrastrukturen

Dieser Artikel bietet Optionen zum Freigeben des Zugriffs für einen Drittanbieter zum Testen/Validieren, wenn Sie ein Problem mit einer Erweiterung für Adobe Commerce in der Cloud-Infrastruktur haben.
Bei der Entscheidung, wie Dritten Zugang gewährt werden soll, sollten Sie sich an die entsprechenden internen Verfahren und Anforderungen zur Datensicherheit halten.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Für Tests zu verwendende Umgebungen

Abhängig von Ihren internen Sicherheitsstandards können Sie die Fehlerbehebung von Drittanbietern in einer lokalen Umgebung durchführen lassen. Wenn das Problem nicht lokal reproduziert werden kann, können Sie Zugriff auf Ihre Cloud-Umgebung gewähren. Wenn Sie sich dafür entscheiden, stellen Sie sicher, dass Sie im Rahmen Ihrer internen Sicherheitsstandards arbeiten. Wenn Sie Zugriff auf eine Ihrer Cloud-Umgebungen gewähren, stellen Sie sicher, dass Ihr Drittanbieter weiß, was getan werden kann und welche Genehmigung für Dinge wie die ausschließliche Replikation oder die Zulassung von Code-Änderungen erforderlich ist. Dies ist besonders für Produktionsumgebungen wichtig.

## Bereitstellung von Zugriff und Daten für Dritte

* Ermöglichen Sie Ihrem Drittanbieter Zugriff auf die Cloud-Umgebung. Verwandte Artikel:

   * [Benutzerhandbuch für Adobe Commerce Help Center > GEMEINSAMER ZUGRIFF: GEWÄHREN SIE ANDEREN BENUTZERN BERECHTIGUNGEN FÜR DEN ZUGRIFF AUF IHR KONTO](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) in unserer Support-Wissensdatenbank.
   * [Freigeben Ihres Commerce](https://experienceleague.adobe.com/de/docs/commerce-admin/start/commerce-account/commerce-account-share) in unserem Benutzerhandbuch.

* Erstellen Sie einen Datenbank-Dump (oder gewähren Sie Drittanbietern Zugriff). Dies kann über die CLI oder in der Commerce Admin Console erfolgen. Dieser DB-Dump verschleiert Kundendaten, sodass sie nur Code- und Produkt-SKUs usw. erhalten, keine proprietären/Kundendaten. Verwenden Sie als Referenz [Sharing Your Commerce Account] (/help/how-to/general/create-database-dump-on-cloud.md) in unserer Support-Wissensdatenbank.
* Nachdem die Tests abgeschlossen sind, stellen Sie sicher, dass Sie den freigegebenen Zugriff auf Ihre Cloud-Umgebung widerrufen, wie in [Benutzerhandbuch für das Adobe Commerce Help Center > Widerrufen (freigegebenen Zugriff löschen)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) in unserer Support-Wissensdatenbank beschrieben.

## Best Practice für Tests

Die Standardpraxis besteht in der Fehlerbehebung in einer lokalen Umgebung. Wenn das Problem nicht lokal reproduziert werden kann, navigieren Sie zu Staging . Der Drittanbieter muss möglicherweise die Produktion überprüfen. Stellen Sie sicher, dass Ihr Drittanbieter weiß, dass er nur versuchen soll, das Problem in Produktion und Staging zu reproduzieren und keine Code-Änderungen vorzunehmen. Wenn er Code-Änderungen vornehmen muss, muss er zunächst Ihre Erlaubnis einholen.

## Verwandtes Lesen

* [Best Practices für die Verwendung von Erweiterungen von Drittanbietern in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) in unserer Support-Wissensdatenbank.
