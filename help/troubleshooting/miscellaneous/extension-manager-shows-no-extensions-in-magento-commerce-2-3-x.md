---
title: Extension Manager zeigt in Adobe Commerce 2.3.x keine Erweiterungen an
description: Dieser Artikel bietet eine Problemumgehung für fehlende Erweiterungen im Admin-Extension Manager in Adobe Commerce 2.3.x, nachdem Sie Erweiterungen über die Commerce Marketplace erworben haben.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager zeigt in Adobe Commerce 2.3.x keine Erweiterungen an

Dieser Artikel bietet eine Problemumgehung für fehlende Erweiterungen im Admin-Extension Manager in Adobe Commerce 2.3.x, nachdem Sie Erweiterungen über die Commerce Marketplace erworben haben.

## Betroffene Produkte und Versionen

* Adobe Commerce-Version (alle Bereitstellungsmethoden) 2.3.x

## Problem

Wenn Sie Erweiterungen über die Commerce Marketplace erwerben, können Sie sie nicht mit dem Adobe Commerce-Extension Manager installieren. Wenn Sie Ihre Zugriffsschlüssel hinzufügen und mit dem Marketplace synchronisieren, zeigt der Extension Manager keine Erweiterungen an.

Die **Problemumgehung** besteht darin, die Befehlszeilen-Adobe Commerce-Installation zu verwenden, wie in [Allgemeine CLI-Installation](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions) in unserer Entwicklerdokumentation beschrieben.

<u>Schritte zur Reproduktion</u>:

1. Erwerben Sie eine Erweiterung über die Commerce Marketplace.
1. Fügen Sie die Zugriffsschlüssel Ihrer Erweiterung hinzu und synchronisieren Sie mit dem Marketplace.
1. Navigieren Sie zum Abschnitt Extension Manager des Admin-Bereichs.

<u>Erwartetes Ergebnis</u>:

Die Erweiterung wird im Abschnitt Extension Manager der Commerce Admin angezeigt.

<u>Tatsächliches </u>:

**Im Abschnitt Extension Manager der Commerce Admin wird keine Erweiterung angezeigt, ähnlich der folgenden Abbildung:**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Abhilfe

Verwenden Sie die Befehlszeilen-Adobe Commerce-Installation, wie unter [Allgemeine CLI-Installation](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions) in unserer Entwicklerdokumentation beschrieben.
