---
title: Fehler 'Die Ortskennzahl ist nicht festgelegt' beim Ausführen des Setups:upgrade
description: Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.2.3 im Zusammenhang mit dem Fehler *Area Code is not set* beim Ausführen des Befehls setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Fehler &#39;Die Ortskennzahl ist nicht festgelegt&#39; bei der Ausführung von `setup:upgrade`

Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.2.3 im Zusammenhang mit dem Abrufen des *Fehlers &quot;* ist nicht festgelegt“ bei Ausführung des folgenden Befehls:

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

wird folgende Fehlermeldung angezeigt: *„MODULE &#39;Magento\_AdvancedSalesRule&#39;: Installing data…Area code not set: Area code must be set before starting a session“* und die Befehlsausführung wird unterbrochen. Das Problem tritt auf, weil die Bereichskonfiguration angefordert wird, bevor sie tatsächlich festgelegt wird. Mit dem Patch kann der Fehler erkannt werden, ohne dass der Upgrade-Prozess unterbrochen wird.

## Fleck

Der Patch ist diesem Artikel beigefügt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch herunterladen](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Kompatible Adobe Commerce-Versionen:

Der Patch wurde erstellt für:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.3

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (kann das Problem jedoch nicht beheben):

* Adobe Commerce on Cloud Infrastructure und Adobe Commerce On-Premises 2.2.0 - 2.2.3

## Anbringen des Pflasters

Anweisungen finden Sie unter [So wenden Sie einen von Adobe bereitgestellten Composer-Patch &#x200B;](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) unserer Support-Wissensdatenbank an.

## Angehängte Dateien
