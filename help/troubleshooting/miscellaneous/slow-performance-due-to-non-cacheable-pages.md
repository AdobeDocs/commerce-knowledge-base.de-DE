---
title: Langsame Leistung aufgrund nicht zwischenspeicherbarer Seiten
description: Dieser Artikel bietet Lösungen für erhöhte Website-Ladezeiten oder Ausfälle, da der vollständige Seiten-Cache (z. B. Fastly) für jeden Block auf allen Seiten, die zwischengespeichert werden müssen, deaktiviert wurde.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Langsame Leistung aufgrund nicht zwischenspeicherbarer Seiten

Dieser Artikel bietet Lösungen für erhöhte Website-Ladezeiten oder Ausfälle, da der vollständige Seiten-Cache (z. B. Fastly) für jeden Block auf allen Seiten, die zwischengespeichert werden müssen, deaktiviert wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premises 2.x.x

### Problem

Die Site weist eine langsame Leistung auf, da es Cache-Blöcke auf Seiten gibt, die zwischenspeicherbar sein müssen, aber auf `cacheable="false"` gesetzt wurden.

### Ursache

Es gibt Seiten, die von Adobe Commerce zwischengespeichert werden müssen. Diese Seiten haben den größten Durchsatz. Jede Anfrage dieser Seitentypen, die nicht aus dem Cache stammt, verlangsamt die Leistung von Adobe Commerce.

Diese Seiten sind:

* Katalogkategorie (PLP)
* Produktdetailseite (PDP)
* Statische Inhaltsseiten (Homepage, Kontakt usw.)

Zwischenspeicherbare und nicht zwischenspeicherbare Begriffe werden verwendet, um anzugeben, ob eine Seite zwischengespeichert werden soll oder nicht. Standardmäßig können alle Seiten zwischengespeichert werden. Wenn jedoch ein Block in einem Layout als nicht cachefähig gekennzeichnet ist, ist die gesamte Seite nicht cachefähig.

Der folgende Screenshot zeigt einen Block mit einer Einstellung `cacheable="false"` **&#x200B; **, durch die eine nicht Cache-taugliche Seite erstellt wird.

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

Beispiele für nicht zwischenspeicherbare Seiten sind Vergleichsprodukte, Warenkorb- und Kaufbestätigungsseiten.

Die folgende Liste von Seiten wird nicht zwischengespeichert (Fastly-, Block- und Layout-Caches werden vermieden). Dies geschieht aufgrund der „zwischenspeicherbaren“ Konfiguration im Layout.

### Lösung

Überprüfen Sie, ob die oben angegebenen Dateien die Einstellung `cacheable="false"` aufweisen. Wenn ja, überprüfen Sie, ob diese Einstellung erforderlich ist.

* Ziehen Sie bei Bedarf stattdessen in Betracht, nicht zwischenspeicherbare Blöcke in den [Mechanismus für private Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) zu verschieben.
* Entfernen Sie bei Bedarf das Attribut `cacheable="false"` und leeren Sie den Layout-Cache.

>[!NOTE]
>
>Für Adobe Commerce ab Cloud-Infrastruktur 2.4.1 können Sie das [Site-Wide Analysis Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) verwenden, um automatisch zu überprüfen, ob Ihr Vollseiten-Cache nicht korrekt konfiguriert ist.

### Verwandtes Lesen

[Übersicht über den Adobe Commerce-](https://developer.adobe.com/commerce/frontend-core/guide/caching/) in unserer Entwicklerdokumentation.
