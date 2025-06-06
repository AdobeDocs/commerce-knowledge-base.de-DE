---
title: Entität Adobe Commerce Backend kann nicht gespeichert werden
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie eine Entität nicht im Adobe Commerce-Backend speichern können. Dies ist beispielsweise der Fall, wenn Sie eine bestimmte Regel „cart_price“ nicht bearbeiten oder speichern können.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Entität Adobe Commerce Backend kann nicht gespeichert werden

Dieser Artikel bietet eine Lösung für den Fall, dass Sie eine Entität nicht im Adobe Commerce-Backend speichern können. Dies ist beispielsweise der Fall, wenn Sie eine bestimmte `cart_price` nicht bearbeiten oder speichern können.

## Betroffene Produkte und Versionen

Dieses Problem kann sich auf alle Adobe Commerce-Versionen auswirken, bei denen die maximale Sitzungsgröße konfiguriert ist. Dies wurde ab Magento Open Source 2.3.7-p1 und Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 hinzugefügt.


## Problem

Wenn Sie versuchen, Ihren Store neu zu konfigurieren, wird die Seite neu geladen und Ihre Änderungen werden nicht gespeichert. Eine Meldung wird in `var/log/system.log` angezeigt:

*[2021-11-27 00:30:52] report.WARNUNG: Sitzungsgröße von 418056 überschritten Zulässige Sitzungsgröße von 256000. [][]*

<u>Schritte zur Reproduktion</u>:

Beispiel für nicht gespeicherte Store-Konfigurationen:

1. Wählen Sie eine Regel im Adobe Commerce Store unter „Produktion“ > **Marketing** > **Warenkorbpreisregeln** aus.
1. Wählen Sie eine Regel aus, legen Sie sie auf *Inaktiv* fest und speichern Sie die Änderung.

<u>Erwartetes Ergebnis</u>:

Die Regel ist auf „Inaktiv“ festgelegt.

<u>Tatsächliches </u>:

* Seite wird ohne Meldung neu geladen.
* Die Regel ist weiterhin auf „aktiv“ festgelegt.

## Ursache

Dieses Problem hängt mit den kürzlich eingeführten neuen Funktionen zusammen, die sich auf die maximale Sitzungsgröße ausgewirkt haben. Siehe [Sitzungsverwaltung](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/security-session-management) in unserer Entwicklerdokumentation.

## Lösung

Erhöhen Sie den Wert „Maximale Sitzungsgröße“ in (**Stores** > **Konfiguration** > **Erweitert** > **System** > **Sicherheit** > Maximale Sitzungsgröße).

## Verwandtes Lesen

* [Marketing-Menü](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/marketing-menu) in unserem Benutzerhandbuch.
