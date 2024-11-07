---
title: Bereitstellungsprobleme in Bezug auf Kontoberechtigungen und Zugriffsschlüssel
description: Dieser Artikel bietet eine Lösung für Probleme bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturen, die durch den Konflikt zwischen Schlüsseleigentum und Zugriff verursacht werden.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Die Cloud-Lizenz ist mit Kontakt A verknüpft (E-Mail-Adresse: *<u>first@e.mail</u>*)

<u>Zu reproduzierende Schritte</u>:

1. Kontakt Ein erstellter Adobe Commerce-Zugriffsschlüssel auf seinem Konto (Schlüssel X) und dessen Installation in der Cloud.
1. Kontakt B (E-Mail-Adresse: *<u>second@e.mail</u>*) hat eine Erweiterung über sein Konto gekauft und die Zugriffsschlüssel für die Installation der Erweiterung erstellt (Schlüssel Y).
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

Wenn Sie keinen Zugriff auf das mit dem alten Schlüssel verknüpfte [Commerce Marketplace](https://marketplace.magento.com/)-Konto haben, wenden Sie sich an den Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), damit der Schlüssel deaktiviert wird.[

Wenn Sie Zugriff auf das mit dem alten Schlüssel verknüpfte Marketplace-Konto haben, führen Sie die folgenden Schritte aus, um den Schlüssel zu deaktivieren:

1. Melden Sie sich mit den Anmeldedaten des alten Kontos bei [Commerce Marketplace](https://marketplace.magento.com/) an.
1. Klicken Sie oben rechts auf der Seite auf den Kontonamen und wählen Sie **Mein Profil** aus.
1. Klicken Sie auf der Registerkarte &quot;Marketplace&quot;auf **Zugriffsschlüssel** .

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Klicken Sie neben dem Zugriffsschlüssel auf **Deaktivieren** .

## Verwandtes Lesen

* [Besorgen Sie sich Ihre Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) in unserer Entwicklerdokumentation.
