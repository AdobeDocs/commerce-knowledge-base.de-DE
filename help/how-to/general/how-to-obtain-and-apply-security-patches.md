---
title: Abrufen und Anwenden von [!UICONTROL security patch]
description: Dieser Artikel enthält Anweisungen zum Abrufen und Anwenden eines [!UICONTROL security patch] , das veröffentlicht wurde, Anweisungen jedoch nicht verfügbar sind.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Abrufen und Anwenden eines [!UICONTROL security patch]

Dieser Artikel enthält Anweisungen zum Abrufen und Anwenden eines [!UICONTROL security patch] , das veröffentlicht wurde, Anweisungen jedoch nicht verfügbar sind.

## Betroffene Produkte und Versionen

Adobe Commerce On-Premise und Cloud - Alle Versionen

## Ursache

Die meisten [!UICONTROL Security Patches] werden ohne jegliche physische Datei oder Hotfix veröffentlicht, die angewendet werden sollen.

## Lösung


### Fall I:

Wenn eine physische Patch-Datei/ein Hotfix in den Versionshinweisen erwähnt wird:

* Laden Sie die Datei aus dem Download-Abschnitt von [https://account.magento.com](https://account.magento.com/downloads/view/) herunter. (Benutzer mit gemeinsamem Zugriff müssen zunächst Download-Berechtigungen vom Kontoinhaber/Lizenzinhaber erhalten.)

**Einschränkungen:**

Wenn Sie eine ältere Version von Adobe Commerce verwenden und den erweiterten Support erworben haben, muss Ihre Version eine der folgenden sein, um die Sicherheitspatches anwenden zu können:

* 2.4.2-p2
* 2.4.3-p3

Wenn Sie keinen erweiterten Support haben, können Sie den Support anfordern, die Patches für Sie freizugeben. Sie können jedoch keine Probleme/Fehler beheben, die bei der Anwendung auftreten können.

### Fall II:

Wenn eine physische Patch-Datei/-Hotfix in den Versionshinweisen nicht erwähnt wird:

* **Cloud:**

1. Einige [!UICONTROL Security Patches] sind möglicherweise in der neuesten Version der Cloud Tools Suite (ECE Tools) unter Cloud Patches für Commerce enthalten/veröffentlicht. Überprüfen Sie die [Versionshinweise](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite). Wenn in der Version eine Sicherheitskorrektur erwähnt wird, aktualisieren Sie das Paket auf diese Version.
1. Wenn in den Versionshinweisen keine Sicherheitskorrektur erwähnt wird, lesen Sie weiter.

* **Cloud oder On-Premise:**

* Wenn keine physische Patch-Datei/kein Hotfix verfügbar ist, aktualisieren Sie die Adobe Commerce-Version auf Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X auf die neueste Patch-Version 2.4.X-pY.[
* Wenn keine physische Patch-Datei/kein Hotfix verfügbar ist, aktualisieren Sie die Adobe Commerce-Version On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X auf die neueste Patch-Version 2.4.X-pY.[

## Verwandtes Lesen

* Siehe [Versionshinweise für Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) im *Handbuch zu Adobe Commerce on Cloud Infrastructure*.
* Siehe [Aktualisieren der Adobe Commerce-Version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) im *Handbuch zu Adobe Commerce on Cloud Infrastructure*.
