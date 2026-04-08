---
title: E-Mail-Adresse des aktuellen Adobe-Kontos ändern
description: Erfahren Sie, wie Sie die aktuelle, im Adobe-Konto registrierte E-Mail-Adresse in eine neue Adresse ändern, die derzeit nicht im Adobe- oder Magento-Konto registriert ist.
exl-id: ca549d38-0d62-4206-9727-0ed85b733dc3
feature: Communications
source-git-commit: 2fc3353c7563cff6fb82236d40a91306523a579e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# E-Mail-Adresse des aktuellen Adobe-Kontos ändern

In diesem Artikel wird erläutert, wie Sie die aktuelle E-Mail-Adresse, die im [Adobe-Konto](https://account.adobe.com/) registriert ist, in eine neue Adresse ändern, die derzeit nicht im [Adobe-Konto](https://account.adobe.com/) oder dem [Magento-Konto registriert ](https://account.magento.com/).

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden und -versionen)

## Voraussetzungen

Der Inhaber der neuen E-Mail-Adresse muss Zugriff auf die aktuelle E-Mail-Adresse haben.

Wenn Sie keinen Zugriff auf die aktuelle E-Mail-Adresse haben, richten Sie mithilfe der E-Mail-Server-Konfiguration des Unternehmens die E-Mail-Weiterleitung von der E-Mail-Adresse des aktuellen Besitzers an eine neue E-Mail-Adresse ein.

## Schritte zum Ändern der E-Mail-Adresse

Gehen Sie wie folgt vor, um die E-Mail-Adresse zu ändern:

1. Setzt das mit der alten E-Mail-Adresse verwendete Passwort zurück. Befolgen Sie die Anweisungen unter [Vergessenes Kennwort zurücksetzen](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html) in der Adobe-Hilfe.
1. Der Link zum Zurücksetzen des Kennworts wird mit Anweisungen an das Postfach des aktuellen Besitzers gesendet.
1. Navigieren Sie zur Seite [Adobe-Konto](https://account.adobe.com), um sich mit der neuen E-Mail anzumelden und das Kennwort einzurichten.

## Wichtig: Der Benutzername des Cloud-Kontos wird nicht automatisch aktualisiert

Wenn Sie Adobe Commerce in der Cloud-Infrastruktur verwenden, wird durch das Ändern der E-Mail-Adresse in Ihrem Adobe-Konto oder der MAGE-ID der in Ihrem [Cloud-Konto](https://accounts.magento.cloud) angezeigte Benutzername nicht automatisch aktualisiert.

Nachdem Sie die Schritte in diesem Artikel zum Ändern der E-Mail-Adresse Ihres Adobe-Kontos ausgeführt haben:

1. Melden Sie sich bei Ihrem Cloud-Konto unter [https://accounts.magento.cloud](https://accounts.magento.cloud) an.
1. Aktualisieren Sie das Cloud-Kontoprofil (Benutzername) manuell, indem Sie die Schritte in [So aktualisieren Sie das Cloud-Kontoprofil](/help/how-to/general/how-to-update-the-cloud-account-profile.md) in unserer Support-Wissensdatenbank ausführen.

Dadurch wird sichergestellt, dass der Benutzername Ihres Cloud-Kontos mit Ihrer aktualisierten Adobe- oder MAGE-ID-E-Mail übereinstimmt, und Verwirrung beim Zugriff auf Cloud-Projekte oder beim Empfang von Systembenachrichtigungen vermieden wird.

## Überprüfen des Zugriffs auf Marketplace und Support nach der E-Mail-Änderung

Nachdem Sie die E-Mail-Adresse für Ihre MAGE-ID geändert haben, müssen Sie auch die folgenden Schritte ausführen, um sicherzustellen, dass Adobe Commerce Marketplace und der Support Ihre neue E-Mail korrekt erkennen:

### Commerce Marketplace-E-Mail verifizieren

1. Melden Sie sich bei [https://commercemarketplace.com/customer/account](https://commercemarketplace.com/customer/account) an und bestätigen Sie, dass Ihre Konto-E-Mail auf die neue Adresse aktualisiert wurde.
1. Wenn die E-Mail nicht aktualisiert wurde, reichen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/support#home) ein, um die E-Mail zum Commerce Marketplace-Konto zu korrigieren.

### Bitten Sie den Support, die Aktualisierung des internen Kontos abzuschließen

1. Senden Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/support#home) mit der Frage, ob wir alle erforderlichen internen Aktualisierungen durchführen sollen (z. B. die Aktualisierung der Verknüpfung zwischen Ihren alten und neuen Adobe-IDs und Ihrer MAGE-ID).
1. Wenn Sie bereits ein Support-Ticket geöffnet haben, da die Commerce Marketplace-E-Mail im vorherigen Abschnitt nicht aktualisiert wurde, können Sie dasselbe Ticket verwenden, um diese zusätzlichen internen Aktualisierungen anzufordern.
