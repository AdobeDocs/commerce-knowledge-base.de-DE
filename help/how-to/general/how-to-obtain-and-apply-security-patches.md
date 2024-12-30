---
title: Abrufen und Anwenden von [!UICONTROL security patch]
description: Dieser Artikel enthält Anweisungen dazu, wie Sie eine freigegebene [!UICONTROL security patch] abrufen und anwenden. Anweisungen hierzu sind jedoch nicht verfügbar.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# So erhalten Sie ein [!UICONTROL security patch] und wenden es an

Dieser Artikel enthält Anweisungen dazu, wie Sie eine freigegebene [!UICONTROL security patch] abrufen und anwenden. Anweisungen hierzu sind jedoch nicht verfügbar.

## Betroffene Produkte und Versionen

Adobe Commerce On-Premise und Cloud - Alle Versionen

## Ursache

Die meisten [!UICONTROL Security Patches] werden ohne physische Datei oder Hotfix veröffentlicht.

## Lösung


### Fall I:

Wenn in den Versionshinweisen eine physische Patch-Datei/ein Hotfix erwähnt wird:

* Laden Sie die Datei aus dem Download-Abschnitt von [https://account.magento.com](https://account.magento.com/downloads/view/) herunter. (Benutzer mit gemeinsamem Zugriff müssen zunächst vom Kontoinhaber/Lizenzinhaber Download-Rechte erhalten.)

**Einschränkungen:**

Wenn Sie eine ältere Version von Adobe Commerce verwenden und erweiterten Support erworben haben, muss Ihre Version eine der folgenden sein, um die Sicherheits-Patches anwenden zu können:

* 2.4.2-p2
* 2.4.3-p3

Wenn Sie nicht über erweiterten Support verfügen, können Sie den Support anfordern, die Patches für Sie freizugeben. Diese können jedoch keine Probleme/Fehler beheben, auf die Sie bei der Anwendung stoßen.

### Fall II:

Wenn in den Versionshinweisen keine physische Patch-Datei bzw. kein Hotfix erwähnt wird:

* **cloud:**

1. Einige [!UICONTROL Security Patches] sind möglicherweise in der neuesten Version von Cloud Tools Suite (ECE-Tools) unter Cloud-Patches für Commerce enthalten/veröffentlicht. Überprüfen Sie die [Versionshinweise](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) und aktualisieren Sie das Paket auf diese Version, wenn in der Version eine Sicherheitskorrektur erwähnt wird.
1. Wenn in den Versionshinweisen keine Sicherheitskorrektur erwähnt wird, lesen Sie weiter.

* **Cloud oder On-Premise:**

* Wenn keine physische Patch-Datei bzw. kein Hotfix verfügbar ist, [aktualisieren Sie die Adobe Commerce-Version auf Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.x auf die neueste Patch-Version 2.4.x-pY.
* Wenn keine physische Patch-Datei bzw. kein Hotfix verfügbar ist, [aktualisieren Sie Adobe Commerce On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X auf die neueste Patch-Version 2.4.X-pY.

## Verwandtes Lesen

* Siehe [Versionshinweise für Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) im *Handbuch zu Adobe Commerce in Cloud Infrastructure*.
* Siehe [Upgrade der Adobe Commerce-Version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) im Handbuch zu *Adobe Commerce in Cloud-Infrastrukturen*.
