---
title: Langsame Leistung aufgrund nicht zwischenspeicherbarer Seiten
description: Dieser Artikel bietet Lösungen für kürzere Ladezeiten von Websites oder Ausfälle, da der vollständige Seiten-Cache (z. B. Fastly) für jeden Block auf allen Seiten deaktiviert wurde, die zwischengespeichert werden müssen.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Der folgende Screenshot zeigt einen Block mit der Einstellung `cacheable="false"` ** **, der eine nicht erreichbare Seite erstellt.

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

Beispiele für nicht erreichbare Seiten sind vergleichende Produkte, Warenkorb und Checkout-Seiten.

Die folgende Liste von Seiten wird nicht zwischengespeichert (Fastly-, Block- und Layout-Caches werden vermieden.) Dies geschieht aufgrund der &quot;zwischenspeicherbaren&quot; Konfiguration im Layout.

### Lösung

Überprüfen Sie, ob die oben angegebenen Dateien die Einstellung `cacheable="false"` aufweisen. Ist dies der Fall, überprüfen Sie, ob diese Einstellung erforderlich oder erforderlich ist.

* Ziehen Sie bei Bedarf stattdessen das Verschieben nicht zwischenspeicherbarer Blöcke in den [Mechanismus für private Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in Erwägung.
* Entfernen Sie bei Bedarf das Attribut `cacheable="false"` und leeren Sie den Layout-Cache.

>[!NOTE]
>
>Für Adobe Commerce in der Cloud-Infrastruktur 2.4.1 und höher können Sie mit dem [Site-weiten Analyse-Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) automatisch überprüfen, ob Ihr vollständiger Seiten-Cache nicht richtig konfiguriert ist.

### Verwandte Informationen

[Überblick über den Adobe Commerce-Cache](https://developer.adobe.com/commerce/frontend-core/guide/caching/) in unserer Entwicklerdokumentation.
