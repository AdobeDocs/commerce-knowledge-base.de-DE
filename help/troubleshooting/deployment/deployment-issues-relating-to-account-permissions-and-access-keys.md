---
title: Bereitstellungsprobleme in Bezug auf Kontoberechtigungen und Zugriffsschlüssel
description: Dieser Artikel bietet eine Lösung für Probleme bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturen, die durch einen Konflikt mit dem Zugriffsschlüssel verursacht wurden.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Bereitstellungsprobleme in Bezug auf Kontoberechtigungen und Zugriffsschlüssel

Dieser Artikel bietet eine Lösung für Probleme bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturen, die durch einen Konflikt mit dem Zugriffsschlüssel verursacht wurden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle unterstützten Versionen

## Problem

<u>Voraussetzungen</u>:

Die Cloud-Lizenz ist mit Kontakt A verknüpft (E-Mail-Adresse: *<u>first@e.mail</u>*)

<u>Schritte zur Reproduktion</u>:

1. Kontaktieren Sie einen erstellten Adobe Commerce-Zugriffsschlüssel in ihrem Konto (Schlüssel X) und installieren Sie ihn in der Cloud.
1. Kontakt B (E-Mail-Adresse: *<u>second@e.mail</u>*) hat mit seinem Konto eine Erweiterung erworben und die Zugriffsschlüssel für die Installation der Erweiterung erstellt (Schlüssel Y).
1. Dann verließ Kontakt A das Unternehmen, und die Lizenz (das Eigentum) wurde dann an Kontakt B übertragen.
1. Systemintegrator versucht, die Erweiterung mithilfe von Schlüssel X in der Cloud-Umgebung zu installieren.

<u>Erwartetes Ergebnis</u>:

Erweiterung wurde erfolgreich installiert.

<u>Tatsächliches </u>:

Die Erweiterung ist nicht installiert, da die Bereitstellung fehlschlägt.

## Ursache

Beide Schlüssel sind der Kontaktrolle zugewiesen, was einen Konflikt verursacht.

## Lösung

Wenn eine Bereitstellung fehlschlug, nachdem eine Änderung am Primären Kontakt für das Konto vorgenommen wurde (wobei sowohl das Originalkonto als auch das neue Konto jeweils über eigene Zugriffsschlüssel verfügen) und die Schlüssel vom Originalkonto auf das neue Konto übertragen wurden, müssen Sie die Schlüssel des Originalkontos deaktivieren. Im obigen Beispiel sollte die Taste X deaktiviert sein.

### Deaktivieren des Zugriffsschlüssels

Wenn Sie keinen Zugriff auf das [Commerce Marketplace](https://marketplace.magento.com/)-Konto haben, das mit dem alten Schlüssel verknüpft ist, [kontaktieren Sie den Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um den Schlüssel zu deaktivieren.

Wenn Sie Zugriff auf das Marketplace-Konto haben, das mit dem alten Schlüssel verknüpft ist, führen Sie die folgenden Schritte aus, um den Schlüssel zu deaktivieren:

1. Melden Sie sich mit den Anmeldeinformationen [&#128279;](https://marketplace.magento.com/) alten Kontos bei der Commerce Marketplace an.
1. Klicken Sie oben rechts auf der Seite auf den Kontonamen und wählen Sie **Mein Profil** aus.
1. Klicken Sie **der Registerkarte** Marketplace“ auf „Zugriffsschlüssel“.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Klicken **neben** Zugriffsschlüssel auf „Deaktivieren“.

## Verwandtes Lesen

* [Erhalten Sie Ihre Authentifizierungsschlüssel](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) in unserer Entwicklerdokumentation.
