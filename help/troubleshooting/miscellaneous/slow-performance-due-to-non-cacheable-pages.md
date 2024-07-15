---
title: Langsame Leistung aufgrund nicht zwischenspeicherbarer Seiten
description: Dieser Artikel bietet Lösungen für kürzere Ladezeiten von Websites oder Ausfälle, da der vollständige Seiten-Cache (z. B. Fastly) für jeden Block auf allen Seiten deaktiviert wurde, die zwischengespeichert werden müssen.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Langsame Leistung aufgrund nicht zwischenspeicherbarer Seiten

Dieser Artikel bietet Lösungen für kürzere Ladezeiten von Websites oder Ausfälle, da der vollständige Seiten-Cache (z. B. Fastly) für jeden Block auf allen Seiten deaktiviert wurde, die zwischengespeichert werden müssen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premise 2.x.x

### Problem

Die Leistung der Site ist langsam, da es Cacheblöcke auf Seiten gibt, die zwischenspeicherbar sein müssen, aber auf `cacheable="false"` gesetzt wurden.

### Ursache

Es gibt Seiten, die von Adobe Commerce zwischengespeichert werden müssen. Diese Seiten weisen den größten Durchsatz auf. Jede Anforderung dieser Seitentypen, die nicht aus dem Cache stammen, führt dazu, dass Adobe Commerce langsamer arbeitet.

Diese Seiten sind:

* Katalogkategorie (PLP)
* Produktdetailseite (PDP)
* Statische Inhaltsseiten (Homepage, Kontakt usw.)

Zwischenspeicherbar und nicht speicherbar sind Begriffe, die angeben, ob eine Seite zwischengespeichert werden soll oder nicht. Standardmäßig sind alle Seiten zwischenspeicherbar. Wenn jedoch ein Baustein in einem Layout als unerreichbar gekennzeichnet ist, ist die gesamte Seite nicht erreichbar.

Der folgende Screenshot zeigt einen Block mit der Einstellung `cacheable="false”` ** **, der eine nicht erreichbare Seite erstellt.

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

Beispiele für nicht erreichbare Seiten sind vergleichende Produkte, Warenkorb und Checkout-Seiten.

Die folgende Liste von Seiten wird nicht zwischengespeichert (Fastly-, Block- und Layout-Caches werden vermieden.) Dies geschieht aufgrund der &quot;zwischenspeicherbaren&quot; Konfiguration im Layout.

### Lösung

Überprüfen Sie, ob die oben angegebenen Dateien die Einstellung `cacheable="false”` aufweisen. Ist dies der Fall, überprüfen Sie, ob diese Einstellung erforderlich oder erforderlich ist.

* Ziehen Sie bei Bedarf stattdessen das Verschieben nicht zwischenspeicherbarer Blöcke in den [Mechanismus für private Inhalte](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=private%20co) in Erwägung.
* Entfernen Sie bei Bedarf das Attribut `cacheable="false”` und leeren Sie den Layout-Cache.

>[!NOTE]
>
>Für Adobe Commerce in der Cloud-Infrastruktur 2.4.1 und höher können Sie mit dem [Site-weiten Analyse-Tool](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) automatisch überprüfen, ob Ihr vollständiger Seiten-Cache nicht richtig konfiguriert ist.

### Verwandte Informationen

[Überblick über den Adobe Commerce-Cache](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=cacheable%2) in unserer Entwicklerdokumentation.
