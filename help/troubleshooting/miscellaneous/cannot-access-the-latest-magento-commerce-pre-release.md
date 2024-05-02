---
title: Zugriff auf die neueste Vorabversion von Adobe Commerce nicht möglich
description: Dieser Artikel bietet Lösungen für Probleme bei der Verwendung des neuesten Pre-Release-Codes von Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Zugriff auf die neueste Vorabversion von Adobe Commerce nicht möglich

Dieser Artikel bietet Lösungen für Probleme bei der Verwendung des neuesten Pre-Release-Codes von Adobe Commerce.

>[!NOTE]
>
>Wenn Sie Probleme mit dem Beta-Zugriff haben, lesen Sie den Abschnitt [Zugriff auf die neueste Beta-Version nicht möglich](/help/how-to/general/cannot-access-the-latest-beta-version.md) Artikel.

## Problem

In diesem Artikel werden die folgenden Probleme beim Zugriff auf den Pre-Release-Code behandelt:

* Sie können den Code vor der Veröffentlichung nicht finden.
* Fehlschlagen des Downloads der frühzeitigen Nutzung der Adobe Commerce-Version von [magento.com](https://account.magento.com/customer/account/login) Verwenden von Composer.

## Ursache

Dies sind die häufigsten Ursachen für Probleme:

* Sie suchen den Code für den frühzeitigen Zugriff an der falschen Stelle.
* Sie verwenden die falsche MageID, wenn Sie über Composer auf den Code zugreifen.
* Ihr Konto ist nicht Teil des Pre-Release-Programms.

## Lösung

### Speicherort des frühzeitigen Zugriffs-Codes

Während der Vorabversion sind Release-Pakete an zwei Orten verfügbar:

1. Über Composer auf [magento.com](https://repo.magento.com/) Verwendung der primären MageID für das Konto. Weitere Informationen zur Verwendung von Composer finden Sie unter [Installieren von Adobe Commerce mithilfe von Composer](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) in unserer Entwicklerdokumentation.
1. **Mein Konto** > **Downloads** on [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Release-Pakete sind auf GitHub erst ab dem GA-Datum verfügbar.

### MageID, die Sie verwenden müssen

Sie müssen die primäre MageID verwenden, die Ihrem Adobe Commerce- oder Partnerkonto zugeordnet ist. Das Vorab-Programm ist nicht mit Kontakten verknüpft, die gemeinsamen Zugriff haben. Der frühzeitige Zugriff ist nur über Composer oder [repo.magento.com](https://repo.magento.com/) durch die mit Ihrer Adobe Commerce-Lizenz oder -Partner-Lizenz verknüpfte MageID.

#### Wie finde ich heraus, ob meine MageID die primäre ID ist?

**Für Händler**

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Anmelden [magento.com](https://account.magento.com/customer/account/login) und gehen Sie zu **Mein Produkt und meine Dienste** Registerkarte. Überprüfen Sie, ob dort die Adobe Commerce-Lizenzinformationen angezeigt werden:
   * Wenn die Adobe Commerce-Lizenzinformationen angezeigt werden, ist Ihre MageID primär.
   * Wenn die Adobe Commerce-Lizenzinformationen nicht angezeigt werden, hat Ihre MageID nur freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zum **Freigegeben für mich** Beachten Sie, dass dort der SHARENAME angegeben ist. Klicks **Wechseln von Konten** und wählen Sie den Wert aus, den Sie in SHARENAME notiert haben. Auf der Begrüßungsseite sehen Sie die E-Mail des primären ID-Inhabers.
1. Falls Sie diese Informationen aus irgendeinem Grund nicht finden können unter [magento.com](https://account.magento.com/customer/account/login), wenden Sie sich bitte an Ihr Adobe-Account-Team.
1. Wenn keines der oben genannten Verfahren funktioniert, bitte [Support kontaktieren](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**Für Partner**

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Anmelden [magento.com](https://account.magento.com/customer/account/login) und gehen Sie zu **Mein Produkt und meine Dienste** Registerkarte. Überprüfen Sie im Unterabschnitt Partner , ob die Informationen zur aktiven Partner-Lizenz angezeigt werden:
   * Wenn die aktiven Partner-Lizenzinformationen angezeigt werden, ist Ihre MageID primär. Die Partner-Lizenz ist aktiv, wenn der Wert des ENDDATUMS ein Datum in der Zukunft ist.
   * Wenn die aktiven Partner-Lizenzinformationen nicht angezeigt werden, hat Ihre MageID nur freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zum **Freigegeben für mich** Beachten Sie, dass dort der SHARENAME angegeben ist. Klicks **Wechseln von Konten** und wählen Sie den Wert aus, den Sie in SHARENAME notiert haben. Auf der Begrüßungsseite sehen Sie die E-Mail des primären ID-Inhabers.
1. Falls Sie diese Informationen aus irgendeinem Grund nicht finden können unter [magento.com](https://account.magento.com/customer/account/login)kontaktieren Sie bitte Ihren Partner-Manager.
1. Wenn keines der oben genannten Verfahren funktioniert, bitte [Unterstützung с Kontakts](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Nicht Teil des Vorversionsprogramms

Um in das Pre-Release Access-Programm aufgenommen zu werden, muss Ihr Unternehmen über ein aktives Adobe Commerce- oder Partnerkonto verfügen, das gut aufgestellt ist. Wenn Sie glauben, dass Sie diese Kriterien erfüllen und nicht auf den Pre-Release-Code zugreifen können, wenden Sie sich an [Support kontaktieren](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit Ihrer MageID.
