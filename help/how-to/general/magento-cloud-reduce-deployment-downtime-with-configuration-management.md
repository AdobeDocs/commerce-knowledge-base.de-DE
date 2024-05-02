---
title: Reduzieren von Bereitstellungsausfällen in Adobe Commerce in der Cloud-Infrastruktur
description: Um Wartungsausfälle erheblich zu reduzieren und eine effiziente Konfiguration Ihres Stores in allen Umgebungen zu ermöglichen, bietet Adobe Commerce in der Cloud-Infrastruktur die Funktion **Konfigurationsverwaltung**. Bei Implementierungen von Adobe Commerce mit der Cloud-Infrastruktur 2.2.x und höher unterstützt diese Funktion Konzepte und Optionen zur Pipeline-Implementierung mit reduzierten Schritten.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Reduzieren von Bereitstellungsausfällen in Adobe Commerce in der Cloud-Infrastruktur

Um Wartungs-Ausfallzeiten erheblich zu reduzieren und eine effiziente Konfiguration Ihres Stores in allen Umgebungen zu ermöglichen, bietet Adobe Commerce in der Cloud-Infrastruktur die **Konfigurationsverwaltung** Funktion. Bei Implementierungen von Adobe Commerce mit der Cloud-Infrastruktur 2.2.x und höher unterstützt diese Funktion Konzepte und Optionen zur Pipeline-Implementierung mit reduzierten Schritten.

## Übersicht

Zu den schmerzhaften und zeitaufwendigen Problemen bei der Bereitstellung Ihres Webspeichers gehören:

* **Anwenden derselben Konfiguration auf alle Umgebungen.** Normalerweise würden Sie Konfigurationen manuell oder durch komplizierte Datenbankaktualisierungen eingeben. Mit Configuration Management exportieren Sie Konfigurationen aus der Datenbank in eine einzelne Datei, um sie später mit Ihrem Code von Ihrer lokalen Entwicklungsumgebung in die Integration, Staging und Produktion zu pushen.

* **Site-Ausfallzeiten bei der Bereitstellung statischer Inhalte.** Normalerweise werden statische Inhalte während der [Bereitstellungsphase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase). Dies kann bis zu 30 Minuten oder länger dauern, was für Unternehmen nicht akzeptabel ist. Die Konfigurationsverwaltung verschiebt die Bereitstellung statischer Inhalte auf [Build-Phase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?#build-phase), was keine Ausfallzeiten erfordert.

## Technologieversionen

* Adobe Commerce auf Cloud-Infrastruktur **2.1.4** und höher für die Konfigurationsverwaltung
* Adobe Commerce auf Cloud-Infrastruktur **2,2** und höher für die Konfiguration/Pipeline-Bereitstellung

## Was ist Configuration Management?

Kurz gesagt: Der Prozess &quot;Configuration Management&quot;(auch als Pipeline-Implementierung bezeichnet) extrahiert alle Konfigurationseinstellungen aus Ihrer Adobe Commerce für die Cloud-Infrastrukturimplementierung (Datenbank) in eine PHP-Datei. Fügen Sie dann die Datei zu Ihrem Git-Commit hinzu und pushen Sie sie über alle Ihre Umgebungen.

Dies bietet die folgenden Vorteile:

* **Konsistente Einstellungen in allen Umgebungen:** Alle Einstellungen, die in die Konfigurationsdatei exportiert werden, werden gesperrt (die entsprechenden Felder im Commerce Admin sind schreibgeschützt), wodurch konsistente Konfigurationen beim Pushen der Datei über alle Umgebungen hinweg sichergestellt werden.
* **Geringere Ausfallzeiten:** Die statische Dateibereitstellung verschiebt sich von der [Bereitstellungsphase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) (was erfordert, dass sich die Site im Wartungsmodus befindet) bis zum [Build-Phase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?#build-phase) (wenn sich die Site nicht im Wartungsmodus befindet und nicht heruntergefahren wird, wenn Fehler oder Probleme auftreten).
* **Geschützte vertrauliche Daten:** mit Adobe Commerce auf Cloud-Infrastruktur 2.2 und höher exportiert der Prozess auch alle sensiblen Daten (z. B. Anmeldedaten für Zahlungsdenn-Gateway) in die `env.php` -Datei. Diese Datei sollte nur in der Umgebung gespeichert werden, in der sie erstellt wurde, und nicht mit Ihren Git-Verzweigungen gesendet werden.

Es wird dringend empfohlen, den Konfigurationsmanagement-Ansatz in Ihrer Implementierung anzuwenden.

## Konfigurationsverwaltung in unserer Entwicklerdokumentation

* [Konfigurationsverwaltung für **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) und [example](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) im *Anleitung zur Adobe Commerce-Cloud-Infrastruktur*
* [Konfigurationsverwaltung für **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) und [example](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) im *Anleitung zur Adobe Commerce-Cloud-Infrastruktur*
* [Upgrade von 2.0.X oder 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) Abschnitt *Aktualisierung von Adobe Commerce auf Cloud-Infrastruktur* topic
* [Pipeline-Bereitstellung](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) im *Konfigurationshandbuch für Adobe Commerce zur Cloud-Infrastruktur* - Für Adobe Commerce in der Cloud-Infrastruktur müssen Sie die Anweisungen in diesem Handbuch nicht befolgen. Der Inhalt dient nur als Referenz. Wir stellen den Build-Server, die Integrationsumgebungen und vieles mehr mit Adobe Commerce in der Cloud-Infrastruktur bereit.
