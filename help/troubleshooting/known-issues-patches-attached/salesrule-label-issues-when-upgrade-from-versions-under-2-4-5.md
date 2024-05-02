---
title: '[!UICONTROL salesRule] Probleme bei der Aktualisierung von Versionen &lt; 2.4.5'
description: Wenden Sie einen Patch an, um mit ** umzugehen[!UICONTROL salesRule]** Probleme bei der Aktualisierung von Adobe Commerce-Versionen &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** Beschriftungsprobleme bei der Aktualisierung von Versionen &lt; 2.4.5

Die **[!UICONTROL salesRule]** Die Funktion zum Etiketten-Staging wurde in Adobe Commerce eingeführt. [2,4,5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). Diese Änderung kann möglicherweise zu Problemen führen, wenn Sie von Adobe Commerce auf eine Version von &lt; 2.4.5 aktualisieren und auf eine Version von >= 2.4.5 aktualisieren. Nach der Aktualisierung besteht die Möglichkeit, dass **[!UICONTROL salesRule]** -Beschriftungen nicht übereinstimmen. Um dieses Problem zu beheben, sollte unmittelbar nach dem Upgrade auf eine neuere Adobe Commerce-Version ein Patch angewendet werden.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur &lt; 2.4.5

## Patch

Verwenden Sie den folgenden angehängten Patch:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Anwenden des Pflasters

1. Führen Sie die Schritte unter [Durchführen eines Upgrades](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) im Commerce-Handbuch.
1. Wenden Sie das angehängte Pflaster vor dem **[!UICONTROL Update metadata]** Phase.
(Sie können auch den Patch anwenden, nachdem Sie die **[!UICONTROL Update metadata]** Phase, dann müssen Sie jedoch `bin/magento setup:upgrade` erneut).
1. Fahren Sie mit den restlichen Schritten unter [Durchführen eines Upgrades](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
