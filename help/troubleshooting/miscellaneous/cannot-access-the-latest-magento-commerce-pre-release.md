---
title: Zugriff auf die neueste Vorabversion von Adobe Commerce nicht möglich
description: Dieser Artikel bietet Lösungen für Probleme bei der Verwendung des neuesten Pre-Release-Codes von Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Zugriff auf die neueste Vorabversion von Adobe Commerce nicht möglich

Dieser Artikel bietet Lösungen für Probleme bei der Verwendung des neuesten Pre-Release-Codes von Adobe Commerce.

>[!NOTE]
>
>Wenn Sie Probleme mit dem Zugriff auf Beta haben, lesen Sie den Artikel [Zugriff auf die neueste Beta-Version nicht möglich](/help/how-to/general/cannot-access-the-latest-beta-version.md) .

## Problem

In diesem Artikel werden die folgenden Probleme beim Zugriff auf den Pre-Release-Code behandelt:

* Sie können den Code vor der Veröffentlichung nicht finden.
* Fehlschlagen des Downloads der frühzeitigen Nutzung der Adobe Commerce-Version von [magento.com](https://account.magento.com/customer/account/login) mithilfe von Composer.

## Ursache

Dies sind die häufigsten Ursachen für Probleme:

* Sie suchen den Code für den frühzeitigen Zugriff an der falschen Stelle.
* Sie verwenden die falsche MageID, wenn Sie über Composer auf den Code zugreifen.
* Ihr Konto ist nicht Teil des Pre-Release-Programms.

## Lösung

### Speicherort des frühzeitigen Zugriffs-Codes

Während der Vorabversion sind Release-Pakete an zwei Orten verfügbar:

1. Über Composer auf [magento.com](https://repo.magento.com/) mit der primären MageID für das Konto. Weitere Informationen zur Verwendung von Composer finden Sie unter [Installieren von Adobe Commerce mit Composer](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) in unserer Entwicklerdokumentation.
1. **Mein Konto** > **Downloads** auf [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Release-Pakete sind auf GitHub erst ab dem GA-Datum verfügbar.

### MageID, die Sie verwenden müssen

Sie müssen die primäre MageID verwenden, die Ihrem Adobe Commerce- oder Partnerkonto zugeordnet ist. Das Vorab-Programm ist nicht mit Kontakten verknüpft, die gemeinsamen Zugriff haben. Der frühzeitige Zugriff ist nur über Composer oder [repo.magento.com](https://repo.magento.com/) über die mit Ihrer Adobe Commerce-Lizenz oder -Partnerlizenz verknüpfte MageID möglich.

#### Wie finde ich heraus, ob meine MageID die primäre ID ist?

**Für Händler**

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Melden Sie sich bei [magento.com](https://account.magento.com/customer/account/login) an und wechseln Sie zur Registerkarte **Mein Produkt und meine Dienste** . Überprüfen Sie, ob dort die Adobe Commerce-Lizenzinformationen angezeigt werden:
   * Wenn die Adobe Commerce-Lizenzinformationen angezeigt werden, ist Ihre MageID primär.
   * Wenn die Adobe Commerce-Lizenzinformationen nicht angezeigt werden, hat Ihre MageID nur freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zu &quot;**Für mich freigegeben**&quot;Beachten Sie den dort angegebenen SHARENAME. Klicken Sie auf **Konten wechseln** und wählen Sie den Wert aus, den Sie in SHARENAME notiert haben. Auf der Begrüßungsseite sehen Sie die E-Mail des primären ID-Inhabers.
1. Sollten Sie diese Informationen aus irgendeinem Grund nicht auf [magento.com](https://account.magento.com/customer/account/login) finden, wenden Sie sich an Ihr Adobe Account Team.
1. Wenn keines der oben genannten Verfahren funktioniert, wenden Sie sich an den Support [1}.](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)

**Für Partner**

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Melden Sie sich bei [magento.com](https://account.magento.com/customer/account/login) an und wechseln Sie zur Registerkarte **Mein Produkt und meine Dienste** . Überprüfen Sie im Unterabschnitt Partner , ob die Informationen zur aktiven Partner-Lizenz angezeigt werden:
   * Wenn die aktiven Partner-Lizenzinformationen angezeigt werden, ist Ihre MageID primär. Die Partner-Lizenz ist aktiv, wenn der Wert des ENDDATUMS ein Datum in der Zukunft ist.
   * Wenn die aktiven Partner-Lizenzinformationen nicht angezeigt werden, hat Ihre MageID nur freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zu &quot;**Für mich freigegeben**&quot;Beachten Sie den dort angegebenen SHARENAME. Klicken Sie auf **Konten wechseln** und wählen Sie den Wert aus, den Sie in SHARENAME notiert haben. Auf der Begrüßungsseite sehen Sie die E-Mail des primären ID-Inhabers.
1. Wenn Sie diese Informationen aus irgendeinem Grund nicht auf [magento.com](https://account.magento.com/customer/account/login) finden, wenden Sie sich an Ihren Partner-Manager.
1. Wenn keines der oben genannten Verfahren funktioniert, kontaktieren Sie bitte [с Support kontaktieren](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Nicht Teil des Vorversionsprogramms

Um in das Pre-Release Access-Programm aufgenommen zu werden, muss Ihr Unternehmen über ein aktives Adobe Commerce- oder Partnerkonto verfügen, das gut aufgestellt ist. Wenn Sie glauben, dass Sie diese Kriterien erfüllen und nicht auf den Pre-Release-Code zugreifen können, wenden Sie sich mit Ihrer MageID an den Support.[](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
