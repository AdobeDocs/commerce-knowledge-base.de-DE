---
title: Bereitstellungsprobleme in Bezug auf Kontoberechtigungen und Zugriffsschlüssel
description: Dieser Artikel bietet eine Lösung für Probleme bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturen, die durch den Konflikt zwischen Schlüsseleigentum und Zugriff verursacht werden.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Bereitstellungsprobleme in Bezug auf Kontoberechtigungen und Zugriffsschlüssel

Dieser Artikel bietet eine Lösung für Probleme bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturen, die durch den Konflikt zwischen Schlüsseleigentum und Zugriff verursacht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle unterstützten Versionen

## Problem

<u>Voraussetzungen</u>:

Die Cloud-Lizenz ist mit Kontakt A (E-Mail-Adresse: *<u>first@e.mail</u>*)

<u>Zu reproduzierende Schritte</u>:

1. Kontakt Ein erstellter Adobe Commerce-Zugriffsschlüssel auf seinem Konto (Schlüssel X) und dessen Installation in der Cloud.
1. Kontakt B (E-Mail-Adresse: *<u>second@e.mail</u>*) eine Erweiterung über sein Konto erworben und die Zugriffsschlüssel für die Installation der Erweiterung erstellt haben (Schlüssel Y).
1. Kontakt A verließ dann das Unternehmen, und die Lizenz (Eigentum) wurde dann an Kontakt B übertragen.
1. Der Systemintegrator versucht, die Erweiterung mithilfe von Schlüssel X in der Cloud-Umgebung zu installieren.

<u>Erwartetes Ergebnis</u>:

Erweiterung wurde erfolgreich installiert.

<u>Tatsächliches Ergebnis</u>:

Die Erweiterung wird nicht installiert, da die Bereitstellung fehlschlägt.

## Ursache

Beide Schlüssel werden der Kontaktrolle zugewiesen, was zu einem Konflikt führt.

## Lösung

Wenn eine Bereitstellung fehlschlug, nachdem eine Änderung am Primären Kontakt für das Konto vorgenommen wurde (wobei sowohl das ursprüngliche als auch das neue Konto jeweils über eigene Zugriffsschlüssel verfügen) und die Schlüssel vom ursprünglichen Konto auf das neue Konto übertragen wurden, müssen Sie die Schlüssel aus dem ursprünglichen Konto deaktivieren. Im obigen Beispiel sollte der Schlüssel X deaktiviert werden.

### Deaktivieren des Zugriffsschlüssels

Wenn Sie keinen Zugriff auf die [Commerce Marketplace](https://marketplace.magento.com/) Konto, das mit dem alten Schlüssel verknüpft ist, [Adobe Commerce Support kontaktieren](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) , damit der Schlüssel deaktiviert wird.

Wenn Sie Zugriff auf das mit dem alten Schlüssel verknüpfte Marketplace-Konto haben, führen Sie die folgenden Schritte aus, um den Schlüssel zu deaktivieren:

1. Melden Sie sich bei [Commerce Marketplace](https://marketplace.magento.com/) mit den Anmeldedaten des alten Kontos.
1. Klicken Sie oben rechts auf der Seite auf den Kontonamen und wählen Sie **Mein Profil**.
1. Klicks **Zugriffsschlüssel** auf der Registerkarte Marketplace .

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Klicks **Deaktivieren** neben dem Zugriffsschlüssel.

## Verwandtes Lesen

* [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/connect-auth.html) in unserer Entwicklerdokumentation.
