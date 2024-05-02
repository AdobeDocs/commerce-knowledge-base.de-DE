---
title: Anmeldung beim Adobe Commerce-Support- oder Cloud-Konto nicht möglich
description: Dieser Artikel bietet eine Lösung für Fälle, in denen Sie Schwierigkeiten haben, sich beim Adobe Commerce-Support oder Ihrem Cloud-Projekt anzumelden.
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Anmeldung beim Adobe Commerce-Support- oder Cloud-Konto nicht möglich

Dieser Artikel bietet eine Lösung für Fälle, in denen Sie Schwierigkeiten haben, sich beim Adobe Commerce-Support oder Ihrem Cloud-Projekt anzumelden.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) alle [unterstützte Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Wenn Sie [https://account.magento.com/customer/account/login/](https://account.magento.com/customer/account/login/) oder [https://accounts.magento.cloud/user](https://accounts.magento.cloud/user) Sie werden feststellen, dass es jetzt ein einheitliches Anmeldeformular gibt und Sie Ihre Anmeldedaten nicht mehr wie bisher eingeben können.

<u>Zu reproduzierende Schritte</u>:

Versuchen Sie, sich bei Ihrem Commerce-Konto anzumelden.

![adobe-login-one](assets/adobe-login-one.png)

<u>Erwartetes Ergebnis</u>:

Anmeldung erfolgreich durchgeführt.

<u>Tatsächliches Ergebnis</u>:

Sie werden zu einer Seite umgeleitet, um sich mit einem Adobe-Konto anzumelden, und die Anmeldedaten funktionieren nicht.

![adobe-login-two](assets/adobe-login-two.png)


## Ursache

Im Rahmen der Integration von Adobe Commerce mit anderen Adobe-Lösungen müssen alle Benutzer eine Adobe-Anmeldung erstellen - falls noch keine vorhanden ist - und dabei dieselbe E-Mail-Adresse verwenden, die mit ihrer MageID verbunden ist.

## Lösung

Sie können sich wie folgt bei dem Konto anmelden:

- Ein bestehendes Adobe-Unternehmens-/Personenkonto.
- Wenn Sie kein Adobe-Konto haben, erstellen Sie eines mit derselben E-Mail-Adresse.

Anweisungen hierzu finden Sie unter [Commerce Identity Manager](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html) in Adobe Experience League.

## Verwandtes Lesen

- [Link Magento.com und Kontoanmeldungen von accounts.magento.cloud](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
