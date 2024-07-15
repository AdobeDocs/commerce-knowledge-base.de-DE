---
title: Extension Manager zeigt keine Erweiterungen in Adobe Commerce 2.3.x an
description: Dieser Artikel bietet eine Problemumgehung für fehlende Erweiterungen im Admin-Extension Manager in Adobe Commerce 2.3.x, nachdem Sie Erweiterungen über die Commerce Marketplace erworben haben.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager zeigt keine Erweiterungen in Adobe Commerce 2.3.x an

Dieser Artikel bietet eine Problemumgehung für fehlende Erweiterungen im Admin-Extension Manager in Adobe Commerce 2.3.x, nachdem Sie Erweiterungen über die Commerce Marketplace erworben haben.

## Betroffene Produkte und Versionen

* Adobe Commerce-Version (alle Bereitstellungsmethoden) 2.3.x

## Problem

Wenn Sie Erweiterungen über die Commerce Marketplace erwerben, können Sie sie nicht mit dem Adobe Commerce-Extension Manager installieren. Wenn Sie Ihre Zugriffsschlüssel hinzufügen und mit Marketplace synchronisieren, zeigt der Extension Manager keine Erweiterungen an.

Die **Problemumgehung** besteht darin, die Befehlszeileninstallation von Adobe Commerce wie in der [allgemeinen CLI-Installation](https://devdocs.magento.com/extensions/install/) in unserer Entwicklerdokumentation beschrieben zu verwenden.

<u>Zu reproduzierende Schritte</u>:

1. Kaufen Sie eine Erweiterung über die Commerce Marketplace.
1. Fügen Sie die Zugriffsschlüssel Ihrer Erweiterung hinzu und synchronisieren Sie sie mit dem Marketplace.
1. Navigieren Sie zum Bereich Extension Manager des Administrators.

<u>Erwartetes Ergebnis</u>:

Die Erweiterung wird im Extension Manager-Bereich des Commerce-Administrators angezeigt.

<u>Tatsächliches Ergebnis</u>:

**Im Extension Manager-Bereich des Commerce-Administrators wird keine Erweiterung angezeigt, ähnlich wie in unten stehendem Bild:**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Workaround

Verwenden Sie die Befehlszeileninstallation von Adobe Commerce, wie in der Entwicklerdokumentation unter [Allgemeine CLI-Installation](https://devdocs.magento.com/extensions/install/) dargestellt.
