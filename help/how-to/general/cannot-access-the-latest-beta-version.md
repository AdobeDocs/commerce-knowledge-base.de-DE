---
title: Zugriff auf die neueste Beta-Version nicht möglich
description: Dieser Artikel bietet Lösungen für Probleme bei der Verwendung der neuesten Beta-Codeversionen für Adobe Commerce. Beta-Code ist nur für offizielle Adobe-Partner verfügbar, die dem unter [Adobe Commerce Beta-Programm](https://github.com/magento/magento2/wiki/Magento-Beta-Program) beschriebenen Prozess gefolgt sind.
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Zugriff auf die neueste Beta-Version nicht möglich

Dieser Artikel bietet Lösungen für Probleme bei der Verwendung der neuesten Beta-Codeversionen für Adobe Commerce. Der Beta-Code ist nur für offizielle Adobe-Partner verfügbar, die dem unter [Adobe Commerce Beta-Programm](https://github.com/magento/magento2/wiki/Magento-Beta-Program) beschriebenen Prozess gefolgt sind.

## Problem

In diesem Artikel werden die folgenden Probleme beim Zugriff auf den Early-Access-Code behandelt:

* Die Adobe Commerce Beta-Version kann nicht unter **Mein Konto** > **Downloads** auf [magento.com) ](https://account.magento.com/customer/account/login) werden.
* Laden der Adobe Commerce-Version mit frühzeitigem Zugriff von [magento.com) ](https://account.magento.com/customer/account/login) Composer fehlgeschlagen.

## Ursache

Dies sind die häufigsten Ursachen für Probleme:

* Sie suchen den Early Access Code am falschen Ort.
* Sie verwenden die falsche MageID.
* Der Entwickler benötigt Zugriffsschlüssel von der richtigen Image-ID.
* Ihr Konto ist nicht Teil des Beta-Programms.

## Lösung

### Code-Speicherort für frühzeitigen Zugriff

Während der Beta-Zugriffsperioden sind Veröffentlichungspakete nur über Composer auf [repo.magento.com](https://repo.magento.com/) verfügbar. Versionspakete sind in diesem Zeitraum nicht auf GitHub- und Adobe Commerce-Portalen verfügbar und werden am GA-Datum an diesen Speicherorten veröffentlicht. Für weitere Informationen über die Verwendung von Composer klicken Sie bitte [hier](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/composer).

### MageID, die Sie verwenden müssen

Sie müssen die primäre MageID verwenden, die mit Ihrem Partnerkonto verknüpft ist. Das Beta-Programm ist mit keinem Kontakt verknüpft, der gemeinsamen Zugriff hat. Der Early Access kann nur über Composer oder [repo.magento.com](https://repo.magento.com/) mit der MageID Ihrer Partnerlizenz aufgerufen werden.

#### Wie finde ich heraus, ob meine MageID die primäre ID ist?

Um herauszufinden, ob Ihre MageID primär ist, versuchen Sie Folgendes:

1. Melden Sie sich bei [magento.com](https://account.magento.com/customer/account/login) an und gehen Sie zur Registerkarte **Meine Produkte und Services** . Überprüfen Sie im Unterabschnitt Partner , ob Sie die Informationen zur aktiven Partnerlizenz sehen:
   * Wenn Sie die Informationen zur aktiven Partnerlizenz sehen, ist Ihre MageID primär. Die Partnerlizenz ist aktiv, wenn das ENDDATUM ein Datum in der Zukunft ist.
   * Wenn die Informationen zur aktiven Partnerlizenz nicht angezeigt werden, verfügt Ihre MageID nur über freigegebenen Zugriff. Um herauszufinden, wer der primäre ID-Inhaber ist, gehen Sie zu **Für mich freigegeben** Beachten Sie den dort angegebenen SHARENAME. Klicken Sie **Konten wechseln** und wählen Sie den Wert aus, den Sie in SHARENAME angegeben haben. Auf der Begrüßungsseite wird die E-Mail-Adresse des primären ID-Inhabers angezeigt.
1. Sollten Sie diese Informationen aus irgendeinem Grund nicht auf [magento.com](https://account.magento.com/customer/account/login) finden, wenden Sie sich bitte an Ihren Partner Manager.
1. Wenn keiner der oben genannten Schritte funktioniert, wenden Sie [an den Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Entwickler hat nicht den richtigen Zugriff auf Schlüssel

Wenn Sie der primäre MageID-Eigentümer sind und einem Entwickler in Ihrem Team Zugriff gewähren müssen, führen Sie die folgenden Schritte aus:

1. Der primäre MageID-Besitzer muss sich bei [account.magento.com](https://account.magento.com/customer/account/login) anmelden.
1. Wählen Sie die Registerkarte **Marketplace** und klicken Sie dann auf **Zugriffsschlüssel**.
1. Wählen **Neuen Zugriffsschlüssel erstellen** aus und benennen Sie ihn.
1. Senden Sie die Schlüssel an Ihren Entwickler.

### Nicht Teil des Early Access-Programms

Unser Beta Access-Programm steht nur unseren Lösungs- und technischen Partnern zur Verfügung, damit diese unseren Vorproduktions-Code auswerten können. Um am Beta Access-Programm teilnehmen zu können, muss Ihr Unternehmen über ein aktives Adobe-Partnerkonto verfügen, das sich in gutem Zustand befindet und die Beta-NDA ([) ](https://github.com/magento/magento2/wiki/Magento-Beta-Program) hat. Wenn Sie glauben, dass Sie diese Kriterien erfüllen und nicht auf den Beta-Code zugreifen können, wenden Sie sich bitte an [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
