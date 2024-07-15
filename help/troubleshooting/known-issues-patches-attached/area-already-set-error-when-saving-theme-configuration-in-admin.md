---
title: Fehler "Bereich bereits festgelegt"beim Speichern der Designkonfiguration in Admin
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.4 in Zusammenhang mit dem Abrufen der Fehlermeldung *"Bereich ist bereits festgelegt"*, wenn versucht wird, ein Design für die standardmäßige Store-Ansicht in der Commerce-Admin festzulegen.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Fehler &quot;Bereich bereits festgelegt&quot;beim Speichern der Designkonfiguration in Admin

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.4 in Zusammenhang mit dem Abrufen der Fehlermeldung &quot;*&quot;Bereich ist bereits festgelegt&quot;* , wenn versucht wird, ein Design für die standardmäßige Store-Ansicht in Commerce Admin festzulegen.

## Problem

Sie erhalten die Fehlermeldung &quot;*Etwas ist beim Speichern dieser Konfiguration schiefgelaufen: Bereich ist bereits festgelegt* &quot;, wenn Sie versuchen, ein Design für die standardmäßige Store-Ansicht festzulegen.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu &quot;**Inhalt**&quot;> &quot;**Design**&quot;> &quot;**Konfiguration**&quot;.
1. Stellen Sie den Konfigurationsbereich auf *Standard-Speicheransicht* ein.
1. Ändern Sie das Design in der Dropdown-Liste **Angewandtes Design** . Beispiel: von *Luma* bis *Leer.*
1. Klicken Sie auf **Konfiguration speichern**.

<u>Erwartetes Ergebnis</u>: Das ausgewählte Design wird auf die standardmäßige Store-Ansicht angewendet.

<u>Tatsächliches Ergebnis</u> : Design wird nicht angewendet, die Fehlermeldung *&quot;Beim Speichern dieser Konfiguration ist etwas schiefgelaufen: Bereich ist bereits festgelegt&quot;* wird angezeigt.

## Patch

Der Patch ist an diesen Artikel angehängt. Klicken Sie zum Herunterladen auf den folgenden Link oder scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf die angehängte Datei:

[MDVA-1106\_EE\_2.2.4\_v1.composer.patch herunterladen](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce in Cloud-Infrastruktur 2.2.4

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur 2.0.X
* Adobe Commerce auf Cloud-Infrastruktur 2.1.X
* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 - 2.2.5
* Adobe Commerce On-Premise 2.0.X
* Adobe Commerce vor Ort 2.1.X
* Adobe Commerce vor Ort 2.2.0 - 2.2.5

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
