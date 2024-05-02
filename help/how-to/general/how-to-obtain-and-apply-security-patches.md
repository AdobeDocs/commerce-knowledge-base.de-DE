---
title: Erhalten und Anwenden [!UICONTROL security patch]
description: Dieser Artikel enthält Anweisungen zum Abrufen und Anwenden einer [!UICONTROL security patch] wurde veröffentlicht, Anweisungen sind jedoch nicht verfügbar.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# So erhalten und anwenden Sie eine [!UICONTROL security patch]

Dieser Artikel enthält Anweisungen zum Abrufen und Anwenden einer [!UICONTROL security patch] wurde veröffentlicht, Anweisungen sind jedoch nicht verfügbar.

## Betroffene Produkte und Versionen

Adobe Commerce On-Premise und Cloud - Alle Versionen

## Ursache

Am meisten [!UICONTROL Security Patches] freigegeben werden, ohne dass eine physische Datei oder ein Hotfix angewendet werden muss.

## Lösung


### Fall I:

Wenn eine physische Patch-Datei/ein Hotfix in den Versionshinweisen erwähnt wird:

* Laden Sie die Datei aus dem Download-Abschnitt von herunter. [https://account.magento.com](https://account.magento.com/downloads/view/). (Benutzer mit gemeinsamem Zugriff müssen zunächst Download-Berechtigungen vom Kontoinhaber/Lizenzinhaber erhalten.)

**Einschränkungen:**

Wenn Sie eine ältere Version von Adobe Commerce verwenden und den erweiterten Support erworben haben, muss Ihre Version eine der folgenden sein, um die Sicherheitspatches anwenden zu können:

* 2.4.2-p2
* 2.4.3-p3

Wenn Sie keinen erweiterten Support haben, können Sie den Support anfordern, die Patches für Sie freizugeben. Sie können jedoch keine Probleme/Fehler beheben, die bei der Anwendung auftreten können.

### Fall II:

Wenn eine physische Patch-Datei/-Hotfix in den Versionshinweisen nicht erwähnt wird:

* **Cloud:**

1. Einige [!UICONTROL Security Patches] möglicherweise in der neuesten Version der Cloud Tools Suite (ECE Tools) unter Cloud Patches für Commerce enthalten oder veröffentlicht werden - überprüfen Sie das [Versionshinweise](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)und wenn in der Version eine Sicherheitskorrektur erwähnt wird, aktualisieren Sie das Paket auf diese Version.
1. Wenn in den Versionshinweisen keine Sicherheitskorrektur erwähnt wird, lesen Sie weiter.

* **Cloud oder On-Premise:**

* Wenn keine physische Patch-Datei/kein Hotfix verfügbar ist, [Upgrade der Adobe Commerce-Version auf Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X auf die neueste Patch-Version 2.4.X-pY.
* Wenn keine physische Patch-Datei/kein Hotfix verfügbar ist, [On-Premise-Upgrade der Adobe Commerce-Version](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X auf die neueste Patch-Version 2.4.X-pY.

## Verwandtes Lesen

* Siehe [Versionshinweise für Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) im *Handbuch zu Adobe Commerce on Cloud Infrastructure*.
* Siehe [Upgrade der Adobe Commerce-Version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) im *Handbuch zu Adobe Commerce on Cloud Infrastructure*.
