---
title: Zugriff auf die neueste Vorabversion von Adobe Commerce nicht möglich
description: Dieser Artikel enthält Lösungen für Probleme bei der Verwendung des neuesten Vorabversions-Codes von Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Zugriff auf die neueste Vorabversion von Adobe Commerce nicht möglich

Dieser Artikel enthält Lösungen für Probleme bei der Verwendung des neuesten Vorabversions-Codes von Adobe Commerce.

>[!NOTE]
>
>Wenn Sie Probleme mit dem Zugriff auf Beta haben, lesen Sie den Artikel [Zugriff auf die neueste Beta-Version nicht möglich](/help/how-to/general/cannot-access-the-latest-beta-version.md).

## Problem

In diesem Artikel werden die folgenden Probleme beim Zugriff auf den Vorabversions-Code behandelt:

* Sie können den Vorabversions-Code nicht finden.
* Laden der Adobe Commerce-Version mit frühzeitigem Zugriff von [magento.com) ](https://account.magento.com/customer/account/login) Composer fehlgeschlagen.

## Ursache

Dies sind die häufigsten Ursachen für Probleme:

* Sie suchen den Early Access Code am falschen Ort.
* Beim Zugriff auf den Code über Composer wird die falsche MageID verwendet.
* Ihr Konto ist nicht Teil des Vorabversionsprogramms.

## Lösung

### Code-Speicherort für frühzeitigen Zugriff

Während der Vorabversion sind Versionspakete an zwei Stellen verfügbar:

1. Über Composer auf [magento.com](https://repo.magento.com/) unter Verwendung der primären MageID für das Konto. Weitere Informationen zur Verwendung von Composer finden Sie unter [ von Adobe Commerce mit ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) in unserer Entwicklerdokumentation.
1. **Mein** > **Downloads** auf [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Versionspakete sind bis zum GA-Datum nicht auf GitHub verfügbar.

### MageID, die Sie verwenden müssen

Sie müssen die primäre MageID verwenden, die mit Ihrem Adobe Commerce- oder Partnerkonto verknüpft ist. Das Vorabversionsprogramm ist mit keinem Kontakt verknüpft, der über gemeinsamen Zugriff verfügt. Der frühzeitige Zugriff kann nur über Composer oder [repo.magento.com) ](https://repo.magento.com/) die MageID erfolgen, die mit Ihrer Adobe Commerce- oder Partnerlizenz verknüpft ist.

#### Wie finde ich heraus, ob meine MageID die primäre ID ist?

**Für Händler**

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Melden Sie sich bei [magento.com](https://account.magento.com/customer/account/login) an und gehen Sie zur Registerkarte **Meine Produkte und Services** . Überprüfen Sie, ob dort die Adobe Commerce-Lizenzinformationen angezeigt werden:
   * Wenn Sie die Adobe Commerce-Lizenzinformationen sehen, ist Ihre MageID primär.
   * Wenn die Adobe Commerce-Lizenzinformationen nicht angezeigt werden, verfügt Ihre MageID nur über freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zu **Für mich freigegeben** Beachten Sie den dort angegebenen SHARENAME. Klicken Sie **Konten wechseln** und wählen Sie den Wert aus, den Sie in SHARENAME angegeben haben. Auf der Begrüßungsseite wird die E-Mail-Adresse des primären ID-Inhabers angezeigt.
1. Sollten Sie diese Informationen nicht auf [magento.com](https://account.magento.com/customer/account/login) finden, wenden Sie sich bitte an Ihr Adobe Account Team.
1. Wenn keiner der oben genannten Schritte funktioniert, wenden Sie [an den Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**Für Partner**

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Melden Sie sich bei [magento.com](https://account.magento.com/customer/account/login) an und gehen Sie zur Registerkarte **Meine Produkte und Services** . Überprüfen Sie im Unterabschnitt Partner , ob Sie die Informationen zur aktiven Partnerlizenz sehen:
   * Wenn Sie die Informationen zur aktiven Partnerlizenz sehen, ist Ihre MageID primär. Die Partnerlizenz ist aktiv, wenn das ENDDATUM ein Datum in der Zukunft ist.
   * Wenn die Informationen zur aktiven Partnerlizenz nicht angezeigt werden, verfügt Ihre MageID nur über freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zu **Für mich freigegeben** Beachten Sie den dort angegebenen SHARENAME. Klicken Sie **Konten wechseln** und wählen Sie den Wert aus, den Sie in SHARENAME angegeben haben. Auf der Begrüßungsseite wird die E-Mail-Adresse des primären ID-Inhabers angezeigt.
1. Sollten Sie diese Informationen aus irgendeinem Grund nicht auf [magento.com](https://account.magento.com/customer/account/login) finden, wenden Sie sich bitte an Ihren Partner Manager.
1. Wenn keiner der oben genannten Punkte funktioniert, wenden Sie [ (с den Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Nicht Teil des Vorabversionsprogramms

Um am Vorabversionsprogramm für den Zugriff teilnehmen zu können, muss Ihr Unternehmen über ein gültiges Adobe Commerce- oder Partnerkonto verfügen. Wenn Sie der Meinung sind, dass Sie diese Kriterien erfüllen und nicht auf den Vorabversions-Code zugreifen können, [ Sie sich mit Ihrer MageID an den ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)-Support.
