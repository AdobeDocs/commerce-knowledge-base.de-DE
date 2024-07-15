---
title: Zugriff auf die neueste Beta-Version nicht möglich
description: Dieser Artikel enthält Lösungen für Probleme bei der Verwendung der neuesten Beta-Codeversionen für Adobe Commerce. Beta-Code ist nur für offizielle Adobe-Partner verfügbar, die den in [Adobe Commerce Beta Program](https://github.com/magento/magento2/wiki/Magento-Beta-Program) beschriebenen Vorgang ausgeführt haben.
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Zugriff auf die neueste Beta-Version nicht möglich

Dieser Artikel enthält Lösungen für Probleme bei der Verwendung der neuesten Beta-Codeversionen für Adobe Commerce. Beta-Code ist nur für offizielle Adobe-Partner verfügbar, die den im [Adobe Commerce Beta-Programm](https://github.com/magento/magento2/wiki/Magento-Beta-Program) beschriebenen Vorgang ausgeführt haben.

## Problem

In diesem Artikel werden die folgenden Probleme beim Zugriff auf den Code für frühzeitigen Zugriff behandelt:

* Die Adobe Commerce Beta-Version kann nicht unter **Mein Konto** > **Downloads** unter [magento.com](https://account.magento.com/customer/account/login) heruntergeladen werden.
* Fehlschlagen des Downloads der frühzeitigen Nutzung der Adobe Commerce-Version von [magento.com](https://account.magento.com/customer/account/login) mithilfe von Composer.

## Ursache

Dies sind die häufigsten Ursachen für Probleme:

* Sie suchen den Code für den frühzeitigen Zugriff an der falschen Stelle.
* Sie verwenden die falsche MageID.
* Entwickler benötigen Zugriffsschlüssel von der richtigen MageID.
* Ihr Konto ist nicht Teil des Beta-Programms.

## Lösung

### Speicherort des frühzeitigen Zugriffs-Codes

Während der Beta-Zugriffsphasen sind Release-Pakete nur über Composer auf [repo.magento.com](https://repo.magento.com/) verfügbar. In diesem Zeitraum sind keine Release-Pakete auf GitHub- und Adobe Commerce-Portalen verfügbar. Wir werden sie am GA-Datum an diesen Speicherorten veröffentlichen. Weitere Informationen zur Verwendung von Composer erhalten Sie, wenn Sie [hier](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) klicken.

### MageID, die Sie verwenden müssen

Sie müssen die mit Ihrem Partnerkonto verknüpfte primäre MageID verwenden. Das Beta-Programm ist nicht mit Kontakten verknüpft, die gemeinsamen Zugriff haben. Der frühzeitige Zugriff ist nur über Composer oder [repo.magento.com](https://repo.magento.com/) über die mit Ihrer Partner-Lizenz verknüpfte MageID möglich.

#### Wie finde ich heraus, ob meine MageID die primäre ID ist?

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Melden Sie sich bei [magento.com](https://account.magento.com/customer/account/login) an und wechseln Sie zur Registerkarte **Mein Produkt und meine Dienste** . Überprüfen Sie im Unterabschnitt Partner , ob die Informationen zur aktiven Partner-Lizenz angezeigt werden:
   * Wenn die aktiven Partner-Lizenzinformationen angezeigt werden, ist Ihre MageID primär. Die Partner-Lizenz ist aktiv, wenn der Wert des ENDDATUMS ein Datum in der Zukunft ist.
   * Wenn die aktiven Partner-Lizenzinformationen nicht angezeigt werden, hat Ihre MageID nur freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zu &quot;**Für mich freigegeben**&quot;Beachten Sie den dort angegebenen SHARENAME. Klicken Sie auf **Konten wechseln** und wählen Sie den Wert aus, den Sie in SHARENAME notiert haben. Auf der Begrüßungsseite sehen Sie die E-Mail des primären ID-Inhabers.
1. Wenn Sie diese Informationen aus irgendeinem Grund nicht auf [magento.com](https://account.magento.com/customer/account/login) finden, wenden Sie sich an Ihren Partner-Manager.
1. Wenn keines der oben genannten Verfahren funktioniert, wenden Sie sich an den Support [1}.](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)

#### Entwickler haben keinen korrekten Zugriff auf Schlüssel

Wenn Sie der primäre Eigentümer von MageID sind und Entwicklern in Ihrem Team Zugriff gewähren müssen, führen Sie die folgenden Schritte aus:

1. Der primäre MageID-Eigentümer muss sich bei [account.magento.com](https://account.magento.com/customer/account/login) anmelden.
1. Wählen Sie die Registerkarte **Marketplace** und klicken Sie dann auf **Zugriffsschlüssel**.
1. Wählen Sie **Neuen Zugriffsschlüssel erstellen** und benennen Sie ihn.
1. Senden Sie die Schlüssel an Ihren Entwickler.

### Kein Bestandteil des Programms für frühzeitigen Zugang

Unser Beta Access-Programm steht nur unseren Lösungs- und technischen Partnern zur Verfügung, damit sie unseren Pre-Production-Code bewerten können. Um in das Beta Access-Programm aufgenommen zu werden, muss Ihr Unternehmen über ein aktives Adobe-Partnerkonto verfügen, das gut aufgestellt ist und die Beta NDA [hier](https://github.com/magento/magento2/wiki/Magento-Beta-Program) unterzeichnet hat. Wenn Sie glauben, dass Sie diese Kriterien erfüllen und nicht auf den Beta-Code zugreifen können, wenden Sie sich an [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
