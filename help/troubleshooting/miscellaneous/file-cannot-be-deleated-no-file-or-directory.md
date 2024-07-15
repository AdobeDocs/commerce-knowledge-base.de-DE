---
title: "Die Datei kann nicht gelöscht werden. Warnung! unlink: Kein solcher Datei- oder Verzeichnisfehler von  [!DNL Admin]"
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem ein Fehler angezeigt wird *Die Datei kann nicht gelöscht werden. Warnung!unlink Kein solcher Datei- oder Verzeichnisfehler* aus dem [!DNL Admin] beim Löschen von [!DNL Javascript/CSS] Leerzeichen.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Die Datei kann nicht gelöscht werden. Warning!unlink: No such file or directory error* from the [!DNL Admin]

Dieser Artikel bietet eine Lösung für das Problem, bei dem der Fehler *Die Datei kann nicht gelöscht werden. Warnung!unlink: Kein solcher Datei- oder Verzeichnisfehler* aus dem [!DNL Commerce Admin], wenn Sie eine [!DNL JavaScript/CSS] Leerung durchführen.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 - 2.4.6, alle Bereitstellungsmethoden

## Problem

Wenn Sie eine [!DNL JS/CSS]-Leerung durchführen, tritt ein Fehler auf:

*Die Datei &quot;/app/pub/static/_cache/merge/.nfsa42d0e64799fd10000001b&quot;kann nicht gelöscht werden. Warnung!unlink(/app/pub/static/cache/merge/.nfsa42d0e64799fd100000001b): Keine solche Datei oder dieses Verzeichnis*

Oder: Sie sehen den oben genannten Fehler im [!DNL Admin] und/oder einen ähnlichen Fehler in [!DNL New Relic] oder in den Bereitstellungsprotokollen.

Oder: Sie können nicht auf die erweiterte Berichterstellung zugreifen und der cron-Auftrag analytics_collect_data schlägt mit diesem Fehler fehl:

*Die Datei &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd4588a000850c0&quot;kann nicht gelöscht werden. Warnung!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0): Keine solche Datei oder Verzeichnis*

<u>Zu reproduzierende Schritte:</u>

Methode 1:

1. Melden Sie sich bei [!DNL Admin] an.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klicken Sie auf **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Methode 2:

1. Melden Sie sich bei [!DNL Admin] an.
1. Gehen Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Nehmen Sie Änderungen an den [!UICONTROL Base URL] oder [!UICONTROL Base URL (Secure)] vor.
1. Klicken Sie auf **[!UICONTROL Save Config]**.

## Lösung

Wenn Sie in der Cloud-Infrastruktur von Adobe Commerce arbeiten und [!DNL magento/magento-cloud-patches] 1.0.22 installiert haben, die den Patch enthalten, müssen Sie ACSD-50165 nicht separat installieren.

Adobe Commerce on Cloud-Infrastruktur: Aktualisieren Sie Cloud-Patches für Commerce auf Version 1.0.22 (**oder neuer**), die folgende Fehlerbehebung enthält: [Cloud-Patches für Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce vor Ort: Wenden Sie ACSD-50165 mithilfe von [Tools für Qualitätspatches > Nutzung](/docs/commerce-operations/tools/quality-patches-tool/usage.html) an. Der Patch ACSD-50165 enthält [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] > Versionshinweise](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) im Handbuch zu Commerce Tools.
* [[!DNL Quality Patches Tool]: Suchen Sie im Commerce Tools-Handbuch nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
