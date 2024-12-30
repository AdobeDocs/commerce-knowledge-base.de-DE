---
title: EU-Kunden können Zahlungen nicht abschließen
description: Dieser Artikel bietet eine Lösung für das Problem, dass Kunden aus der Europäischen Union keine Zahlungen abschließen können.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# EU-Kunden können Zahlungen nicht abschließen

Dieser Artikel bietet eine Lösung für das Problem, dass Kunden aus der Europäischen Union keine Zahlungen abschließen können.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen
* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problem

Kunden aus der EU beschweren sich, dass ihre Kreditkartentransaktionen abgelehnt werden.

## Ursache

Die Europäische Union hat eine Verordnung mit der Bezeichnung „Zahlungsdiensterichtlinie (PSD)“ mit einer aktualisierten Fassung [PSD2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN) überarbeitet. Dies ist eine Richtlinie der Europäischen Union (EU) zur Regulierung von Zahlungsdiensten und Zahlungsdienstleistern in der gesamten EU und im Europäischen Wirtschaftsraum (EWR). Eine starke Kundenauthentifizierung (SCA) ist eine Voraussetzung von PSD2, um die Sicherheit und Authentifizierung von Zahlungsdaten zu erhöhen. Wenn Ihre Zahlungslösungen nicht den Anforderungen der Richtlinie entsprechen, kann dies dazu führen, dass Kunden Zahlungen nicht abschließen können. Weitere Einzelheiten finden Sie im [zugehörigen Adobe Commerce DevBlog-Beitrag](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Lösung

Befolgen Sie die Empfehlungen aus dem Abschnitt [Adobe Commerce Payment Provider Recommendations des DevBlogs](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
