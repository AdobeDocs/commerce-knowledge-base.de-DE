---
title: 'Die Datei kann nicht gelöscht werden. Warnung! Unlink: Keine derartige Datei oder Verzeichnisfehler im [!DNL Admin]'
description: Dieser Artikel bietet eine Lösung für das Problem, dass ein Fehler angezeigt wird. *Die Datei kann nicht gelöscht werden. Warnung!Unlink No such file or directory error* from the [!DNL Admin] when you do a [!DNL Javascript/CSS] flush.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Die Datei kann nicht gelöscht werden. Warnung!unlink: Kein solcher Datei- oder* im [!DNL Admin]

Dieser Artikel bietet eine Lösung für den Fall, dass ein Fehler angezeigt wird *Die Datei kann nicht gelöscht werden. Warnung!unlink: Kein solcher Datei- oder* aus dem [!DNL Commerce Admin], wenn Sie eine [!DNL JavaScript/CSS] Leerung durchführen.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 - 2.4.6, alle Bereitstellungsmethoden

## Problem

Beim Ausführen einer [!DNL JS/CSS] Flush tritt ein Fehler auf:

*Die Datei &quot;/app/pub/static/_cache/merged/.nfsa42d064799fd1000000001b“ kann nicht gelöscht werden. Warnung!unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b): Keine derartige Datei oder derartiges Verzeichnis*

Oder: Der obige Fehler wird in der [!DNL Admin] und/oder ein ähnlicher Fehler in der [!DNL New Relic] oder in den Bereitstellungsprotokollen angezeigt.

Oder: Sie können nicht auf erweiterte Berichte zugreifen, und der Cron-Vorgang analytics_collect_data schlägt mit diesem Fehler fehl:

*Die Datei &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0“ kann nicht gelöscht werden. Warnung!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): Keine derartige Datei oder derartiges Verzeichnis*

<u>Schritte zur Reproduktion:</u>

Methode 1:

1. Melden Sie sich beim [!DNL Admin] an.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klicken Sie auf **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Methode 2:

1. Melden Sie sich beim [!DNL Admin] an.
1. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Nehmen Sie Änderungen am [!UICONTROL Base URL] oder [!UICONTROL Base URL (Secure)] vor.
1. Klicken Sie auf **[!UICONTROL Save Config]**.

## Lösung

Wenn Sie sich in der Cloud-Infrastruktur von Adobe Commerce befinden und [!DNL magento/magento-cloud-patches] 1.0.22 installiert haben, die den Patch enthalten, müssen Sie ACSD-50165 nicht separat installieren.

Adobe Commerce auf Cloud-Infrastruktur: Aktualisieren Sie Cloud-Patches für Commerce auf 1.0.22 (**oder höher**), das diese Fehlerbehebung enthält: [Cloud-Patches für Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce On-Premise: Wenden Sie ACSD-50165 mithilfe von [Quality Patches Tools > Usage](/docs/commerce-operations/tools/quality-patches-tool/usage.html) an. Der Patch ACSD-50165 ist im Lieferumfang von [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30) enthalten

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] > Versionshinweise](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) im Handbuch zu Commerce-Tools.
* [[!DNL Quality Patches Tool]: Suchen Sie im Handbuch ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) Commerce-Tools nach Patches.
