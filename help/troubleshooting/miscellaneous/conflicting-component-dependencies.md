---
title: Konflikt bei Komponentenabhängigkeiten
description: Dieser Artikel bietet eine Lösung für in Konflikt stehende Komponentenabhängigkeiten. Beim Versuch, Adobe Commerce mit dem Web-Einrichtungs-Assistenten einzurichten oder zu aktualisieren, wird die Fehlermeldung *"Es wurden in Konflikt stehende Komponentenabhängigkeiten gefunden"* Composer angezeigt.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Konflikt bei Komponentenabhängigkeiten

Dieser Artikel bietet eine Lösung für in Konflikt stehende Komponentenabhängigkeiten. Beim Versuch, Adobe Commerce mit dem Web-Einrichtungs-Assistenten einzurichten oder zu aktualisieren, wird die Fehlermeldung &quot;*In Konflikt stehende Komponentenabhängigkeiten&quot;* Composer angezeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Problem {#issue}

Fehlermeldung über in Konflikt stehende Komponentenabhängigkeiten ähnlich der folgenden (tatsächliche Paketnamen und -versionen variieren):

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Ursache

Diese Meldung wird angezeigt, wenn der Composer nicht ermitteln kann, welche Komponenten installiert oder aktualisiert werden sollen.

## Lösung

Zwei Hauptszenarien können zu widersprüchlichen Komponentenabhängigkeiten führen. Klicken Sie auf Ihr Szenario, um Schritte zur Fehlerbehebung zu erhalten.

* [Upgrade von Adobe Commerce](#upgrading-magento)
* [Inkompatibilität mit Drittanbietermodulen:](#incompatibility-third-party-modules)
   * [Adobe Commerce (alle Bereitstellungstypen)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Upgrade von Adobe Commerce {#upgrading-magento}

Wenn Sie Adobe Commerce auf Cloud-Infrastruktur aktualisieren, versuchen Sie Folgendes, um in Konflikt stehende Komponentenabhängigkeiten zu lösen:

* Überprüfen Sie die Schlüssel, die für die Aktualisierung verwendet werden. Werden die Schlüssel aus dem richtigen E-Mail-Konto generiert?
* Überprüfen Sie die Berechtigungen und stellen Sie sicher, dass sie den Magento-Upgrade-Anforderungen entsprechen. Lesen Sie [Magento Upgrade-Übersicht > Checkliste für Aktualisierung und Aktualisierung > Dateisystemberechtigungen](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) in unserer Entwicklerdokumentation.

## Inkompatibilität mit Drittanbietermodulen: {#incompatibility-third-party-modules}

Konflikte zwischen Komponentenabhängigkeiten können auch durch Drittanbietermodule verursacht werden, die von früheren Commerce-Komponenten als den installierten abhängen. Versuchen Sie Folgendes:

1. Im vorherigen [Beispiel](#issue) kann die installierte Paket-Magento/sample-data-Version 0.74.0-beta15 nicht auf 1.0.0-beta aktualisiert werden. 0.74.0-beta15 kann jedoch auf 0.74.0-beta16 (oder andere) aktualisiert werden. Bearbeiten Sie `composer.json` , um eine dieser Änderungen vorzunehmen. In der Regel werden die Versionen, die Ihr Projekt anfordert, in der Eigenschaft `require` oder `require-dev` des Objekts in dieser JSON-Datei definiert. Abhängig von den verfügbaren Optionen der Paketversionen können sie eine bestimmte Version oder eine Einschränkung angeben. Allgemeine Anleitungen zur Verwendung von Composer finden Sie in unserer Entwicklerdokumentation unter [Cloud für Adobe Commerce > Technologien und Anforderungen > Composer](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) . Wenn Sie sich vor Ort in Adobe Commerce befinden, finden Sie weitere Informationen unter [Adobe Commerce > Installationsanleitung > Adobe Commerce mithilfe des Composers installieren](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. Versuchen Sie jetzt die Überprüfung der Bereitschaft. Lesen Sie den Abschnitt [Adobe Commerce-Upgrade-Übersicht > Ausführen des Modulmanagers > Schritt 1 - Prüfung der Bereitschaft](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) in unserer Entwicklerdokumentation.
1. Wenn die Bereitschaftsprüfung mit einer anderen Fehlermeldung zur Komponentenabhängigkeit fehlschlägt, klicken Sie auf die folgenden Links, je nachdem, ob Sie [Adobe Commerce](#magento-commerce-magento-commerce-cloud) oder [Magento Open Source](#opensource) verwenden, um weitere Schritte zur Fehlerbehebung zu erhalten.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Wenden Sie sich an den Entwickler der Erweiterung, damit dieser Ihnen helfen kann. Sie finden ihre Kontaktinformationen auf der Seite, von der Sie die Erweiterung erworben haben, auf der Commerce Marketplace. Suchen Sie nach der Schaltfläche **Verkäufer kontaktieren** , die im rechten Fensterbereich angezeigt wird. Alle Commerce-Entwickler müssen beim Veröffentlichen einer Erweiterung in Marketplace ein Benutzer- und Installationshandbuch bereitstellen. Sie finden beide auf der rechten Seite der Landingpage.
1. Wenn Sie nicht innerhalb einer angemessenen Frist eine Antwort vom Verkäufer erhalten, wenden Sie sich bitte an den Support von Marketplace](mailto:commercemarketplacesupport@adobe.com), damit wir sie an ihre Support-Verpflichtungen beim Kunden erinnern können.[

## Magento Open Source {#opensource}

Fordern Sie Hilfe bei [unserem Hauptforum](https://community.magento.com/) an oder [wenden Sie sich an einen Adobe Commerce-Partner](https://magento.com/find-a-partner), der bei Open Source-Problemen unterstützt.
