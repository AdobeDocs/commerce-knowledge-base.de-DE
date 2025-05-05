---
title: Probleme mit [!UICONTROL salesRule] beim Upgrade von Versionen &lt; 2.4.5
description: Patch anwenden, um die **[!UICONTROL salesRule]**-Probleme beim Upgrade von Adobe Commerce-Versionen &lt; 2.4.5 zu beheben.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Probleme mit **[!UICONTROL salesRule]**-Kennzeichnungen beim Upgrade von Versionen &lt; 2.4.5

Die Staging-Funktion für **[!UICONTROL salesRule]** Bezeichnungen wurde in Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html) eingeführt. Die Änderung kann möglicherweise zu Problemen führen, wenn Sie von Adobe Commerce &lt; 2.4.5 auf eine beliebige Version >= 2.4.5 aktualisieren. Nach dem Upgrade besteht die Möglichkeit, dass **[!UICONTROL salesRule]** Kennzeichnungen nicht übereinstimmen. Um das Problem zu beheben, sollte direkt nach dem Upgrade auf eine neuere Adobe Commerce-Version ein Patch angewendet werden.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur &lt; 2.4.5

## Fleck

Verwenden Sie das folgende beigefügte Pflaster:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Anbringen des Pflasters

1. Führen Sie die Schritte unter [Durchführen eines Upgrades](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=de) im Commerce-Handbuch aus.
1. Kleben Sie das beigefügte Pflaster vor der **[!UICONTROL Update metadata]** auf.
(Sie können den Patch auch anwenden, nachdem Sie die **[!UICONTROL Update metadata]** Phase abgeschlossen haben, aber dann müssen Sie `bin/magento setup:upgrade` erneut ausführen.)
1. Fahren Sie mit den übrigen Schritten in fort [Führen Sie ein Upgrade durch](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=de).
