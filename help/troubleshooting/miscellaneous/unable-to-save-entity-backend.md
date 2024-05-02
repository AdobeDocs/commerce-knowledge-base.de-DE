---
title: Entität Adobe Commerce-Backend kann nicht gespeichert werden
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie eine Entität nicht im Adobe Commerce-Backend speichern können. Wenn Sie beispielsweise eine bestimmte Regel "cart_price"nicht bearbeiten und speichern können.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Entität Adobe Commerce-Backend kann nicht gespeichert werden

Dieser Artikel bietet eine Lösung für den Fall, dass Sie eine Entität nicht im Adobe Commerce-Backend speichern können. Wenn Sie beispielsweise eine bestimmte `cart_price` Regel.

## Betroffene Produkte und Versionen

Dieses Problem kann sich auf alle Adobe Commerce-Versionen auswirken, für die die maximale Sitzungsgröße konfiguriert ist. Dies wurde ab Magento Open Source 2.3.7-p1 und Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 hinzugefügt.


## Problem

Wenn Sie versuchen, Ihren Store neu zu konfigurieren, wird die Seite neu geladen und Ihre Änderungen werden nicht gespeichert. Eine Nachricht wird in `var/log/system.log`:

*[27.11.2021 00:30:52] report.WARNING: Die Sitzungsgröße von 418056 hat die zulässige Sitzungsmax.-Größe von 256000 überschritten. [][]*

<u>Zu reproduzierende Schritte</u>:

Beispiel für eine nicht gespeicherte Speicherkonfiguration:

1. Wählen Sie eine Regel im Adobe Commerce Store unter Produktion > aus. **Marketing** > **Preisregeln für Warenkorb**.
1. Wählen Sie eine Regel aus und legen Sie *Inaaktiv* und speichern Sie die Änderung.

<u>Erwartetes Ergebnis</u>:

Die Regel ist auf &quot;Inaktiv&quot;eingestellt.

<u>Tatsächliches Ergebnis</u>:

* Seiten werden ohne Meldung neu geladen.
* Die Regel ist weiterhin auf &quot;aktiv&quot;eingestellt.

## Ursache

Dieses Problem bezieht sich auf die kürzlich eingeführten neuen Funktionen, die sich auf die maximale Sitzungsgröße ausgewirkt haben. Siehe [Sitzungsverwaltung](https://docs.magento.com/user-guide/stores/security-session-management.html) in unserer Entwicklerdokumentation.

## Lösung

Erhöhen Sie den Wert &quot;Max. Sitzungsgröße&quot;in (**Stores** > **Konfiguration** > **Erweitert** > **System** > **Sicherheit** > Max. Sitzungsgröße).

## Verwandtes Lesen

* [Marketing-Menü](https://docs.magento.com/user-guide/marketing/marketing-menu.html) in unserem Benutzerhandbuch.
