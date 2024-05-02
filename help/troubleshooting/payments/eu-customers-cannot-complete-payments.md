---
title: EU-Kunden können Zahlungen nicht abschließen
description: Dieser Artikel enthält eine Korrektur für das Problem, dass Kunden aus der Europäischen Union nicht in der Lage sind, Zahlungen abzuschließen.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# EU-Kunden können Zahlungen nicht abschließen

Dieser Artikel enthält eine Korrektur für das Problem, dass Kunden aus der Europäischen Union nicht in der Lage sind, Zahlungen abzuschließen.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen
* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problem

Kunden aus der EU beklagen, dass ihre Kreditkartentransaktionen abgelehnt werden.

## Ursache

Die Europäische Union überarbeitete eine Verordnung mit der Bezeichnung Zahlungsdiensterichtlinie (PSD) mit einer aktualisierten Fassung [PSD2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN). Dies ist eine EU-Richtlinie, die zur Regulierung von Zahlungsdiensten und Zahlungsdienstleistern in der gesamten EU und im Europäischen Wirtschaftsraum (EWR) durchgesetzt wird. Starke Kundenauthentifizierung (SCA) ist eine Voraussetzung für PSD2, um die Sicherheit und Authentifizierung von Zahlungsdaten zu erhöhen. Wenn Ihre Zahlungslösungen nicht den Anforderungen der Richtlinie entsprechen, kann dies dazu führen, dass Kunden Zahlungen nicht ausführen können. Weitere Informationen finden Sie unter [verwandter Adobe Commerce DevBlog-Beitrag](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Lösung

Befolgen Sie die Empfehlungen aus dem [Adobe Commerce Payment Provider Recommendations im Abschnitt &quot;DevBlog&quot;](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
