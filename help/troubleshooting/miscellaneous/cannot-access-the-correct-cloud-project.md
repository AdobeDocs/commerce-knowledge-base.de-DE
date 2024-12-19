---
title: Kein Zugriff auf das richtige Adobe Commerce-Konto/Projekt möglich, oder das Projekt fehlt im Konto.
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie nicht auf das richtige Cloud Adobe Commerce-Projekt zugreifen können, wenn sich die Eigentümerschaft ändert oder sich die E-Mail-Adressen ändern.
exl-id: 165b9a18-6e84-4f0f-b377-a07152d55c9e
hide: true
hidefromtoc: true
feature: Cloud, Paas
role: Developer
source-git-commit: 423a392eb32df69c38b84081ac2ed17ae1efdc7b
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Kein Zugriff auf das richtige Cloud-Konto/Projekt möglich, oder das Projekt fehlt im Konto.

Dieser Artikel bietet eine Fehlerbehebung für die folgenden Probleme, nachdem der Kontoinhaber oder die zugehörigen E-Mail-Adressen geändert wurden:

1. Sie können nicht auf die richtigen Cloud Adobe Commerce-Projekte zugreifen.
1. Unter Ihrem Konto bei [accounts.magento.cloud/user](https://accounts.magento.cloud/user) werden keine Cloud-Adobe Commerce-Projekte angezeigt.
1. Die Details eines anderen Kontos (d. h. des vorherigen Kontoinhabers) werden unter &quot;[.magento.cloud/user“ ](https://accounts.magento.cloud/user).

## Problem

Sie können nicht auf das richtige Cloud Adobe Commerce-Projekt zugreifen, wenn sich die Eigentümerschaft ändert oder sich die E-Mail-Adressen ändern.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Ursache

Dieses Problem tritt in der Regel auf, wenn das Single Sign-on (SSO) des vorherigen Projektbesitzers nach dem folgenden Schritt noch in Adobe.com integriert ist:

1. Die Verantwortung für das Cloud-Projekt wurde auf Sie (den Benutzer) übertragen, und Sie sehen das Konto des ursprünglichen Projektbesitzers. Klicken Sie hier für die [Lösung](#solution-for-cause-one-and-two).

   ODER

1. Sie (die Benutzerin bzw. der Benutzer) sind in ein anderes Unternehmen umgezogen, wobei sich die E-Mail-Adresse und die Projekte, auf die Sie Zugriff haben, geändert haben. Sie sehen die Projekte, auf die Sie in Ihrer vorherigen Rolle/Firma Zugriff erhalten hatten. Klicken Sie hier für die [Lösung](#solution-for-cause-one-and-two).

   ODER

1. Sie haben Ihre E-Mail-Adresse unter https://account.adobe.com in eine andere E-Mail-Adresse geändert, die derzeit nicht mit einem Cloud-Projekt verknüpft ist. Klicken Sie hier für die [Lösung](#solution-for-cause-three).

## Lösung für Ursache eins und zwei {#solution-for-cause-one-and-two}

Die Lösung für den Fall, dass das Problem von Eins und Zwei verursacht wird, besteht darin, die Single-Sign-On-Integration von Adobe.com zu trennen. Gehen Sie wie folgt vor, um die Verbindung zu trennen:

1. Erweitern Sie von https://accounts.magento.cloud/user aus den Abschnitt **[!UICONTROL Single Sign-On]** . Klicken Sie auf **[!UICONTROL Disconnect from Adobe.com]**, um die Verbindung zu trennen.

   ![Single-Sign-on-Adobe-Connect](assets/sso-adobe-disconnect.png)

1. Klicken Sie auf **[!UICONTROL Disconnect]**.

   ![adobe-disconnect](assets/adobe-disconnect.png)

1. Abmelden.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Adobe.com]** .

   ![Magento.com](assets/adobe-welcome-login.png)

1. Sie sollten jetzt in der Lage sein, das richtige Konto anzuzeigen und auf das richtige Cloud-Projekt zuzugreifen.

## Lösung für Ursache drei {#solution-for-cause-three}

Wenn das Problem durch Ursache 3 verursacht wurde, bitten Sie einen vorhandenen Super-Benutzer im Projekt, Ihre neue E-Mail-Adresse zum Projekt hinzuzufügen. Weitere Informationen finden Sie unter [Benutzerzugriff verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
