---
title: Verkürzung der Bereitstellungsausfallzeiten auf Adobe Commerce auf Cloud-Infrastrukturen
description: Um Wartungsausfälle erheblich zu reduzieren und eine effiziente Konfiguration Ihres Stores über Umgebungen hinweg bereitzustellen, bietet Adobe Commerce in der Cloud-Infrastruktur die Funktion **Konfigurationsverwaltung**. Bei Implementierungen von Adobe Commerce auf Cloud-Infrastrukturen der Version 2.2.x und höher unterstützt diese Funktion Konzepte und Optionen der Pipeline-Bereitstellung mit reduzierten Schritten.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Verkürzung der Bereitstellungsausfallzeiten auf Adobe Commerce auf Cloud-Infrastrukturen

Um Wartungsausfälle erheblich zu reduzieren und eine effiziente Konfiguration Ihres Stores über Umgebungen hinweg bereitzustellen, bietet Adobe Commerce in der Cloud-Infrastruktur die Funktion **Konfigurationsverwaltung**. Bei Implementierungen von Adobe Commerce auf Cloud-Infrastrukturen der Version 2.2.x und höher unterstützt diese Funktion Konzepte und Optionen der Pipeline-Bereitstellung mit reduzierten Schritten.

## Übersicht

Zu den schmerzhaften und zeitaufwendigen Problemen bei der Bereitstellung Ihres Web Stores gehören:

* **Anwenden derselben Konfiguration auf alle Umgebungen.** Normalerweise würden Sie Konfigurationen manuell oder durch komplizierte Datenbankaktualisierungen eingeben. Mit Configuration Management exportieren Sie Konfigurationen aus der Datenbank in eine einzelne Datei, um sie später mit Ihrem Code aus Ihrer lokalen Entwicklungsumgebung in die Integration, Staging und Produktion zu übertragen.

* **Site-Ausfallzeiten bei der Bereitstellung statischer Inhalte.** In der Regel werden statische Inhalte während der Bereitstellungsphase [bereitgestellt](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Dies kann bis zu 30 Minuten oder länger dauern, was für Unternehmen nicht akzeptabel ist. Die Konfigurationsverwaltung verschiebt die Bereitstellung statischer Inhalte in die [Build-Phase](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), die keine Ausfallzeiten erfordert.

## Technische Versionen

* Adobe Commerce auf Cloud-Infrastruktur **2.1.4** und höher für die Konfigurationsverwaltung
* Adobe Commerce auf Cloud-Infrastruktur **2.2** und höher für die Konfigurationsverwaltung/Pipeline-Bereitstellung

## Was ist Konfigurationsverwaltung?

Um es kurz zu machen: Der Prozess zur Konfigurationsverwaltung (auch als Pipeline-Bereitstellung bezeichnet) extrahiert alle Konfigurationseinstellungen aus Ihrer Adobe Commerce in der Cloud-Infrastrukturimplementierung (Datenbank) in eine einzige PHP-Datei. Anschließend fügen Sie die Datei zu Ihrem Git-Commit hinzu und übertragen sie in alle Ihre Umgebungen.

Dies bietet die folgenden Vorteile:

* **Konsistente Einstellungen in allen Umgebungen:** Alle Einstellungen, die in die Konfigurationsdatei exportiert werden, werden gesperrt (die entsprechenden Felder in Commerce Admin werden schreibgeschützt). Dies stellt konsistente Konfigurationen sicher, wenn Sie die Datei über alle Umgebungen pushen.
* **Geringere Ausfallzeiten:** Die statische Dateibereitstellung wechselt von der [Bereitstellungsphase](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (für die sich die Site im Wartungsmodus befinden muss) in die [Build-Phase](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (wenn sich die Site nicht im Wartungsmodus befindet und nicht heruntergefahren wird, wenn Fehler oder Probleme auftreten).
* **Geschützte sensible Daten:** Mit Adobe Commerce auf Cloud-Infrastruktur 2.2 und höher exportiert der Prozess auch alle sensiblen Daten (z. B. Payment Gateway-Anmeldeinformationen) in die `env.php`. Diese Datei sollte nur in der Umgebung gespeichert werden, in der sie erstellt wurde, und nicht mit Ihren Git-Verzweigungen gepusht werden.

Es wird dringend empfohlen, den Ansatz der Konfigurationsverwaltung in Ihrer -Bereitstellung anzuwenden.

## Konfigurationsverwaltung in unserer Entwicklerdokumentation

* [Konfigurationsverwaltung für **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=de) und das [Beispiel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=de) im Handbuch zu *Adobe Commerce in Cloud-Infrastrukturen*
* [Konfigurationsverwaltung für **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=de) und das [Beispiel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=de) im Handbuch zu *Adobe Commerce in Cloud-Infrastrukturen*
* [Upgrade von 2.0.X oder 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=de#upgrade-from-older-versions) Abschnitt zum Thema *Upgrade von Adobe Commerce auf Cloud-*&quot;
* [Pipeline-Bereitstellung](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html?lang=de) im *Konfigurationshandbuch für Adobe Commerce in der Cloud-Infrastruktur* - Für Adobe Commerce in der Cloud-Infrastruktur müssen Sie die Anweisungen in diesem Handbuch nicht befolgen. Der Inhalt dient ausschließlich als Referenz. Wir bieten den Build-Server, Integrationsumgebungen und mehr bereits mit Adobe Commerce in der Cloud-Infrastruktur an.
