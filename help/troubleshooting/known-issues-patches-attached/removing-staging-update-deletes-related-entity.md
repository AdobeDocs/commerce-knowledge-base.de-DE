---
title: Durch das Entfernen der Staging-Aktualisierung werden verwandte Entitäten gelöscht
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem in Bezug auf die Entität (Kategorie, CMS-Seite usw.) selbst entfernt werden, wenn die zugehörige Zeitplanaktualisierung gelöscht wird.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Durch das Entfernen der Staging-Aktualisierung werden verwandte Entitäten gelöscht

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem in Bezug auf die Entität (Kategorie, CMS-Seite usw.) selbst entfernt werden, wenn die zugehörige Zeitplanaktualisierung gelöscht wird.

>[!NOTE]
>
>Das Problem wurde in Adobe Commerce 2.2.6 behoben.

## Problem

Wenn Sie ein aktives Planupdate zwischen Start- und Enddatum löschen, wird auch die zugehörige Entität (Kategorie, Unterkategorie, CMS-Seite) gelöscht.

<u>Zu reproduzierende Schritte (mit Kategorien)</u>:

1. Melden Sie sich bei Commerce Admin an.
1. Erstellen Sie eine neue Unterkategorie unter **Katalog** > **Kategorien**.
1. Erstellen Sie ein neues Staging-Update mit der Start- und Endzeit.
1. Warten Sie, bis die Aktualisierung durchgeführt wurde. Dies ist die Startzeit.
1. Löschen Sie die Aktualisierung mithilfe des Links **Anzeigen/Bearbeiten** .

<u>Erwartete Ergebnisse</u>:

Die Aktualisierung wird gelöscht und die Unterkategorie ist weiterhin im Admin vorhanden.

<u>Tatsächliche Ergebnisse</u>:

Die Aktualisierung und die Unterkategorie werden gelöscht.

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an und leeren Sie den laufenden Cache-Speicher.

```bash
bin/magento
  cache:clean
```

## Patch

Die Patches sind diesem Artikel beigefügt. Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den entsprechenden Link:

* [MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch herunterladen](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch herunterladen](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Die Patches wurden für Folgendes erstellt:

* MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch wurde für Adobe Commerce erstellt (alle Bereitstellungsmethoden) 2.2.3
* MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch wurde für Adobe Commerce erstellt (alle Bereitstellungsmethoden) 2.2.4
* MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch wurde für Adobe Commerce erstellt (alle Bereitstellungsmethoden) 2.2.5

Der Patch MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch ist ebenfalls mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem aber möglicherweise nicht):

* Adobe Commerce vor Ort 2.2.0-2.2.2
* Adobe Commerce auf Cloud-Infrastruktur 2.2.0-2.2.3

Der Patch MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch ist ebenfalls mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem aber möglicherweise nicht):

* Adobe Commerce vor Ort 2.1.0-2.1.18, 2.2.0-2.2.3
* Adobe Commerce auf Cloud-Infrastruktur 2.1.0-2.1.18, 2.2.0-2.2.3

Der Patch MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch ist ebenfalls mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem aber möglicherweise nicht):

* Adobe Commerce in Cloud-Infrastruktur 2.2.5

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached Files
