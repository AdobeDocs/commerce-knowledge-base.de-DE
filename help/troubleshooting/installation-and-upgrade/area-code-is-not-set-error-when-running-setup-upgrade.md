---
title: "'Bereichscode ist nicht festgelegt'-Fehler beim Ausführen von Setup:upgrade"
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.3 in Zusammenhang mit dem Fehler "Bereichscode ist nicht festgelegt"beim Ausführen des Befehls setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Fehler &quot;Bereichscode ist nicht festgelegt&quot;bei Ausführung von `setup:upgrade`

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.3 in Zusammenhang mit dem Abrufen des Fehlers &quot;*&quot;Area code is not set&quot;*&quot;, wenn der folgende Befehl ausgeführt wird:

```bash
setup:upgrade
```

>[!NOTE]
>
>Das Problem wurde in Adobe Commerce 2.2.4 behoben.

## Problem

Beim Ausführen von

```bash
bin/magento setup:upgrade
```

erhalten Sie die folgende Fehlermeldung: *&quot;Modul &#39;Magento\_AdvancedSalesRule&#39;: Installieren von Daten...Gebietscode nicht festgelegt: Gebietscode muss vor Beginn einer Sitzung festgelegt werden&quot;* und die Ausführung des Befehls wird unterbrochen. Das Problem wird angezeigt, da die Bereichskonfiguration angefordert wird, bevor sie tatsächlich festgelegt wird. Der Patch ermöglicht das Auffinden des Fehlers und nicht das Unterbrechen des Aktualisierungsprozesses.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch herunterladen](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce in Cloud-Infrastruktur 2.2.3

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.2.0 - 2.2.3

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
