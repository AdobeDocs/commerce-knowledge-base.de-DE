---
title: Reduzieren von Bereitstellungsausfällen in Adobe Commerce in der Cloud-Infrastruktur
description: Um Wartungsausfälle erheblich zu reduzieren und eine effiziente Konfiguration Ihres Stores in allen Umgebungen zu ermöglichen, bietet Adobe Commerce in der Cloud-Infrastruktur die Funktion **Konfigurationsverwaltung**. Bei Implementierungen von Adobe Commerce mit der Cloud-Infrastruktur 2.2.x und höher unterstützt diese Funktion Konzepte und Optionen zur Pipeline-Implementierung mit reduzierten Schritten.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Reduzieren von Bereitstellungsausfällen in Adobe Commerce in der Cloud-Infrastruktur

Um Wartungsausfälle erheblich zu reduzieren und eine effiziente Konfiguration Ihres Stores in allen Umgebungen zu ermöglichen, bietet Adobe Commerce in der Cloud-Infrastruktur die Funktion **Konfigurationsverwaltung** . Bei Implementierungen von Adobe Commerce mit der Cloud-Infrastruktur 2.2.x und höher unterstützt diese Funktion Konzepte und Optionen zur Pipeline-Implementierung mit reduzierten Schritten.

## Übersicht

Zu den schmerzhaften und zeitaufwendigen Problemen bei der Bereitstellung Ihres Webspeichers gehören:

* **Anwenden derselben Konfiguration auf alle Umgebungen.** Normalerweise würden Sie Konfigurationen manuell oder durch komplizierte Datenbankaktualisierungen eingeben. Mit Configuration Management exportieren Sie Konfigurationen aus der Datenbank in eine einzelne Datei, um sie später mit Ihrem Code von Ihrer lokalen Entwicklungsumgebung in die Integration, Staging und Produktion zu pushen.

* **Site-Ausfallzeiten bei der Bereitstellung statischer Inhalte.** Normalerweise werden statische Inhalte während der [Bereitstellungsphase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) bereitgestellt. Dies kann bis zu 30 Minuten oder länger dauern, was für Unternehmen nicht akzeptabel ist. Configuration Management verschiebt die Bereitstellung statischer Inhalte in die [Build-Phase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), für die keine Ausfallzeiten erforderlich sind.

## Technologieversionen

* Adobe Commerce für Cloud-Infrastruktur **2.1.4** und höher für Configuration Management
* Adobe Commerce für die Cloud-Infrastruktur **2.2** und höher für die Konfigurationsverwaltung/Pipeline-Bereitstellung

## Was ist Configuration Management?

Kurz gesagt: Der Prozess &quot;Configuration Management&quot;(auch als Pipeline-Implementierung bezeichnet) extrahiert alle Konfigurationseinstellungen aus Ihrer Adobe Commerce für die Cloud-Infrastrukturimplementierung (Datenbank) in eine PHP-Datei. Fügen Sie dann die Datei zu Ihrem Git-Commit hinzu und pushen Sie sie über alle Ihre Umgebungen.

Dies bietet die folgenden Vorteile:

* **Konsistente Einstellungen in allen Umgebungen:** Alle Einstellungen, die in die Konfigurationsdatei exportiert werden, werden gesperrt (die entsprechenden Felder im Commerce Admin sind schreibgeschützt), wodurch konsistente Konfigurationen beim Pushen der Datei in allen Umgebungen gewährleistet sind.
* **Reduzierte Ausfallzeit:** Die Bereitstellung statischer Dateien erfolgt von der [Bereitstellungsphase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (für die die Site im Wartungsmodus sein muss) in die [Build-Phase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (wenn sich die Site nicht im Wartungsmodus befindet und nicht heruntergefahren wird, wenn Fehler oder Probleme auftreten).
* **Geschützte vertrauliche Daten:** Mit Adobe Commerce in der Cloud-Infrastruktur 2.2 und höher exportiert der Prozess auch alle sensiblen Daten (z. B. Payment Gateway-Anmeldeinformationen) in die Datei `env.php`. Diese Datei sollte nur in der Umgebung gespeichert werden, in der sie erstellt wurde, und nicht mit Ihren Git-Verzweigungen gesendet werden.

Es wird dringend empfohlen, den Konfigurationsmanagement-Ansatz in Ihrer Implementierung anzuwenden.

## Konfigurationsverwaltung in unserer Entwicklerdokumentation

* [Konfigurationsverwaltung für **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) und das [Beispiel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) im *Adobe Commerce on Cloud Infrastructure Guide*
* [Konfigurationsverwaltung für **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) und das [Beispiel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) im *Adobe Commerce on Cloud Infrastructure Guide*
* Aktualisierung von 2.0.X oder 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) im Abschnitt *Aktualisieren von Adobe Commerce auf Cloud-Infrastruktur*[
* [Pipeline-Implementierung](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) im *Adobe Commerce on Cloud Infrastructure Configuration Guide* - Für Adobe Commerce on Cloud Infrastructure müssen Sie die Anweisungen in diesem Handbuch nicht befolgen. Der Inhalt dient nur als Referenz. Wir stellen den Build-Server, die Integrationsumgebungen und vieles mehr mit Adobe Commerce in der Cloud-Infrastruktur bereit.
