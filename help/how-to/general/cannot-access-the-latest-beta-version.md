---
title: Zugriff auf die neueste Beta-Version nicht möglich
description: Dieser Artikel enthält Lösungen für Probleme bei der Verwendung der neuesten Beta-Versionen von Code für Adobe Commerce. Beta-Code ist nur für offizielle Adobe-Partner verfügbar, die den in [Adobe Commerce Beta Program](https://github.com/magento/magento2/wiki/Magento-Beta-Program) beschriebenen Prozess befolgt haben.
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Zugriff auf die neueste Beta-Version nicht möglich

Dieser Artikel enthält Lösungen für Probleme bei der Verwendung der neuesten Beta-Versionen von Code für Adobe Commerce. Beta-Code ist nur für offizielle Adobe-Partner verfügbar, die den in [Adobe Commerce Beta-Programm](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problem

In diesem Artikel werden die folgenden Probleme beim Zugriff auf den Code für frühzeitigen Zugriff behandelt:

* Adobe Commerce Beta-Version kann nicht heruntergeladen werden unter **Mein Konto** > **Downloads** on [magento.com](https://account.magento.com/customer/account/login).
* Fehlschlagen des Downloads der frühzeitigen Nutzung der Adobe Commerce-Version von [magento.com](https://account.magento.com/customer/account/login) Verwenden von Composer.

## Ursache

Dies sind die häufigsten Ursachen für Probleme:

* Sie suchen den Code für den frühzeitigen Zugriff an der falschen Stelle.
* Sie verwenden die falsche MageID.
* Entwickler benötigen Zugriffsschlüssel von der richtigen MageID.
* Ihr Konto ist nicht Teil des Beta-Programms.

## Lösung

### Speicherort des frühzeitigen Zugriffs-Codes

Während der Beta-Zugriffsphasen sind Release-Pakete nur über Composer auf verfügbar [repo.magento.com](https://repo.magento.com/). In diesem Zeitraum sind keine Release-Pakete auf GitHub- und Adobe Commerce-Portalen verfügbar. Wir werden sie am GA-Datum an diesen Speicherorten veröffentlichen. Weitere Informationen zur Verwendung von Composer finden Sie unter [here](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### MageID, die Sie verwenden müssen

Sie müssen die mit Ihrem Partnerkonto verknüpfte primäre MageID verwenden. Das Beta-Programm ist nicht mit Kontakten verknüpft, die gemeinsamen Zugriff haben. Der frühzeitige Zugriff ist nur über Composer oder [repo.magento.com](https://repo.magento.com/) durch die mit Ihrer Partner-Lizenz verknüpfte MageID.

#### Wie finde ich heraus, ob meine MageID die primäre ID ist?

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Anmelden [magento.com](https://account.magento.com/customer/account/login) und gehen Sie zu **Mein Produkt und meine Dienste** Registerkarte. Überprüfen Sie im Unterabschnitt Partner , ob die Informationen zur aktiven Partner-Lizenz angezeigt werden:
   * Wenn die aktiven Partner-Lizenzinformationen angezeigt werden, ist Ihre MageID primär. Die Partner-Lizenz ist aktiv, wenn der Wert des ENDDATUMS ein Datum in der Zukunft ist.
   * Wenn die aktiven Partner-Lizenzinformationen nicht angezeigt werden, hat Ihre MageID nur freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zum **Freigegeben für mich** Beachten Sie, dass dort der SHARENAME angegeben ist. Klicks **Wechseln von Konten** und wählen Sie den Wert aus, den Sie in SHARENAME notiert haben. Auf der Begrüßungsseite sehen Sie die E-Mail des primären ID-Inhabers.
1. Falls Sie diese Informationen aus irgendeinem Grund nicht finden können unter [magento.com](https://account.magento.com/customer/account/login)kontaktieren Sie bitte Ihren Partner-Manager.
1. Wenn keines der oben genannten Verfahren funktioniert, bitte [Support kontaktieren](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Entwickler haben keinen korrekten Zugriff auf Schlüssel

Wenn Sie der primäre Eigentümer von MageID sind und Entwicklern in Ihrem Team Zugriff gewähren müssen, führen Sie die folgenden Schritte aus:

1. Die primäre Anmeldung des MageID-Eigentümers bei [account.magento.com](https://account.magento.com/customer/account/login).
1. Wählen Sie die **Marketplace** und klicken Sie auf **Zugriffsschlüssel**.
1. Auswählen **Neuen Zugriffsschlüssel erstellen** und benennen Sie sie.
1. Senden Sie die Schlüssel an Ihren Entwickler.

### Kein Bestandteil des Programms für frühzeitigen Zugang

Unser Beta Access Programm steht nur unseren Lösungen und technischen Partnern zur Verfügung, damit sie unseren Vorproduktionscode auswerten können. Um in das Beta-Zugriffsprogramm aufgenommen zu werden, muss Ihr Unternehmen über ein aktives Adobe-Partner-Konto verfügen, das gut aufgestellt ist und die Beta-NDA unterzeichnet hat [here](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Wenn Sie glauben, dass Sie diese Kriterien erfüllen und nicht auf den Beta-Code zugreifen können, wenden Sie sich an [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
