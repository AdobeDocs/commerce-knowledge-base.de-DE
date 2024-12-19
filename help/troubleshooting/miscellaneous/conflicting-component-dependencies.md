---
title: Widersprüchliche Komponentenabhängigkeiten
description: Dieser Artikel bietet eine Lösung für kollidierende Komponentenabhängigkeiten. Beim Versuch, Adobe Commerce mithilfe des Websetup-Assistenten einzurichten oder zu aktualisieren, wird die Fehlermeldung *„We found conflicting component dependencies“* Composer angezeigt.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Widersprüchliche Komponentenabhängigkeiten

Dieser Artikel bietet eine Lösung für kollidierende Komponentenabhängigkeiten. Beim Versuch, Adobe Commerce mithilfe des Websetup-Assistenten einzurichten oder zu aktualisieren, wird die *„We found conflicting component dependencies“* Composer-Fehlermeldung angezeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Problem {#issue}

Fehlermeldung zu widersprüchlichen Komponentenabhängigkeiten ähnlich der folgenden (tatsächliche Paketnamen und -versionen variieren):

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Ursache

Diese Meldung wird angezeigt, wenn Composer nicht ermitteln kann, welche Komponenten installiert oder aktualisiert werden sollen.

## Lösung

Zwei Hauptszenarien können zu widersprüchlichen Komponentenabhängigkeiten führen. Klicken Sie auf Ihr Szenario, um Schritte zur Fehlerbehebung zu erhalten.

* [Aktualisieren von Adobe Commerce](#upgrading-magento)
* [Inkompatibilität mit Modulen von Drittanbietern:](#incompatibility-third-party-modules)
   * [Adobe Commerce (alle Bereitstellungstypen)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Aktualisieren von Adobe Commerce {#upgrading-magento}

Wenn Sie ein Upgrade von Adobe Commerce auf Cloud-Infrastruktur durchführen, versuchen Sie Folgendes, um widersprüchliche Komponentenabhängigkeiten zu beheben:

* Markieren Sie die Schlüssel, die für die Aktualisierung verwendet werden. Werden die Schlüssel aus dem richtigen E-Mail-Konto generiert?
* Überprüfen Sie die Berechtigungen und stellen Sie sicher, dass sie den Magento-Upgrade-Anforderungen entsprechen. Lesen Sie [Übersicht über das Magento-Upgrade > Checkliste für Aktualisierung und Upgrade > Dateisystemberechtigungen](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites#verify-file-system-permissions) in unserer Entwicklerdokumentation.

## Inkompatibilität mit Modulen von Drittanbietern: {#incompatibility-third-party-modules}

Konflikte zwischen Komponentenabhängigkeiten können auch durch Drittanbietermodule verursacht werden, die von älteren Commerce-Komponenten als den von Ihnen installierten abhängen. Probieren Sie Folgendes aus:

1. Im vorherigen [Beispiel](#issue) kann das installierte Paket magento/sample-data der Version 0.74.0-beta15 nicht auf 1.0.0-beta aktualisiert werden. 0.74.0-beta15 kann jedoch auf 0.74.0-beta16 (oder andere) aktualisiert werden. Bearbeiten Sie `composer.json`, um eine dieser Änderungen vorzunehmen. Normalerweise werden die Versionen, die Ihr Projekt anfordert, in der `require`- oder `require-dev`-Eigenschaft des -Objekts in dieser JSON-Datei definiert. Je nach den Optionen der bereitgestellten Paketversionen können sie eine bestimmte Version oder eine Einschränkung angeben. Allgemeine Anleitungen zur Verwendung von Composer finden Sie unter „Cloud für Adobe Commerce&quot; > „Technologien und Anforderungen“ > &quot;[&quot; in ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#files) Entwicklerdokumentation. Wenn Sie Adobe Commerce On-Premise verwenden, lesen Sie [Adobe Commerce > Installationshandbuch > Adobe Commerce mithilfe des Composers installieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) .
1. Jetzt die Bereitschaftsprüfung versuchen. Lesen Sie [Überblick über das Adobe Commerce-Upgrade > Ausführen des Modul-Managers > Schritt 1-](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/overview) in unserer Entwicklerdokumentation.
1. Wenn die Bereitschaftsprüfung mit einer anderen Fehlermeldung für die Komponentenabhängigkeitsprüfung fehlschlägt, klicken Sie auf die folgenden Links, je nachdem, ob Sie [Adobe Commerce](#magento-commerce-magento-commerce-cloud) oder [Magento Open Source ](#opensource) verwenden, um weitere Schritte zur Fehlerbehebung zu erhalten.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Wenden Sie sich an den Entwickler der Erweiterung, damit er Ihnen helfen kann. Die Kontaktinformationen finden Sie auf der Seite, von der Sie die Erweiterung gekauft haben, auf der Commerce Marketplace. Suchen Sie nach der Schaltfläche **Verkäufer kontaktieren**, die auf der rechten Seite angezeigt wird. Alle Commerce-Entwicklerinnen und -Entwickler müssen beim Veröffentlichen einer Erweiterung auf dem Marketplace ein Benutzer- und Installationshandbuch bereitstellen. Sie finden beide auf der rechten Seite ihrer Landingpage.
1. Wenn Sie vom Verkäufer nicht innerhalb einer angemessenen Zeit eine Antwort erhalten, wenden Sie sich bitte [an den Marketplace-Support](mailto:commercemarketplacesupport@adobe.com), damit wir ihn an seine Kundensupportverpflichtungen erinnern können.

## Magento Open Source {#opensource}

Fordern Sie Hilfe an [unser Hauptforum](https://community.magento.com/) oder [kontaktieren Sie einen Adobe Commerce-Partner](https://magento.com/find-a-partner) der bei offenen Source-Problemen hilft.
