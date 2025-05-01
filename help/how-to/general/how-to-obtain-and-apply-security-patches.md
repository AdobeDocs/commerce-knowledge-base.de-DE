---
title: Abrufen und Anwenden von [!UICONTROL security patch]
description: Dieser Artikel enthält Anweisungen dazu, wie Sie eine freigegebene [!UICONTROL security patch] abrufen und anwenden. Anweisungen hierzu sind jedoch nicht verfügbar.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 3c7234b52e5e4465d95c95345e1c070c28600dfb
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# So erhalten Sie ein [!UICONTROL security patch] und wenden es an

>[!NOTE]
>Wenn Sie eine On-Premise-Installation haben und keine Versionskontrollsysteme wie [!DNL CVS] oder [!DNL GitHub] verwenden, um Ihren Code zu verwalten, kann Ihr Webhost möglicherweise bei der Anwendung des Patches helfen. Sie können sich gerne an sie wenden, um Unterstützung zu erhalten.

Dieser Artikel enthält Anweisungen dazu, wie Sie eine freigegebene [!UICONTROL security patch] abrufen und anwenden. Anweisungen hierzu sind jedoch nicht verfügbar.

## Betroffene Produkte und Versionen

Adobe Commerce On-Premise und Cloud - Alle Versionen


## Ursache

Die meisten [!UICONTROL Security Patches] werden ohne einen isolierten Patch oder Hotfix veröffentlicht und müssen auf die [!UICONTROL Security Patch] Version aktualisiert werden.

## Lösung


### Fall I:

* Wenn in den [Versionshinweisen eine isolierte Patch-Datei/ein Hotfix erwähnt wird](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) laden Sie die Datei aus dem Download-Abschnitt von [https://account.magento.com](https://account.magento.com/downloads/view/) herunter. Benutzer mit gemeinsamem Zugriff müssen zunächst vom Kontoinhaber bzw. Lizenzinhaber über Download-Rechte verfügen.

**Einschränkungen:**

Wenn Sie eine ältere Version von Adobe Commerce (2.4.4) verwenden, erhalten Sie automatisch erweiterte Unterstützung. Ihre Version muss eine der folgenden nicht unterstützten Versionen sein, um die neuesten verfügbaren Sicherheits-Patches anwenden zu können:

2.4.4 - 2.4.4-P11

Nicht unterstützte Versionen (2.3.x, 2.4.0 - 2.4.3) sind nicht unterstützungsfähig, und Sie müssen zunächst ein Upgrade auf eine unterstützte Version durchführen, um die neuesten Sicherheitskorrekturen nutzen zu können.

Wenn Sie nicht über erweiterten Support verfügen, können Sie den Support anfordern, die Patches für Sie freizugeben. Diese können jedoch keine Probleme/Fehler beheben, auf die Sie bei der Anwendung stoßen.

### Fall II:

Isolierte Patches werden nur in Ausnahmefällen bereitgestellt und sind nicht die bevorzugte Form der Implementierung von Sicherheitskorrekturen.

Wenn in den Versionshinweisen keine einzelne Patch-Datei bzw. kein Hotfix erwähnt wird:

* **cloud:**

1. Einige [!UICONTROL Security Patches] sind möglicherweise in der neuesten Version von Cloud Tools Suite (ECE-Tools) unter Cloud-Patches für Commerce enthalten/veröffentlicht. Überprüfen Sie die [Versionshinweise](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) und aktualisieren Sie das Paket auf diese Version, wenn in der Version eine Sicherheitskorrektur erwähnt wird.
1. Wenn in den Versionshinweisen keine Sicherheitskorrektur erwähnt wird, lesen Sie weiter.

* **Cloud oder On-Premise:**

* Wenn keine isolierte Patch-Datei bzw. kein Hotfix verfügbar ist, [aktualisieren Sie die Adobe Commerce-Version auf Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X auf die neueste Patch-Version 2.4.X-pY.
* Wenn keine isolierte Patch-Datei bzw. kein Hotfix verfügbar ist, [aktualisieren Sie Adobe Commerce On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X auf die neueste Patch-Version 2.4.X-pY.

## Verwandtes Lesen

* Siehe [Versionshinweise für Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) im *Handbuch zu Adobe Commerce in Cloud-Infrastrukturen*.
* Siehe [Upgrade der Adobe Commerce-Version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) im Handbuch zu *Adobe Commerce in Cloud-Infrastrukturen*.
