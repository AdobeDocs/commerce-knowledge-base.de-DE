---
title: Web-API kann Anfragen mit mehr als 20 Elementen im Array nicht verarbeiten
description: Dieser Artikel bietet eine Lösung für das Problem, dass die Web-API eine Nachricht, die mehr als 20 Elemente im Array für Adobe Commerce 2.4.3 enthält, nicht verarbeiten kann.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Web-API kann Anfragen mit mehr als 20 Elementen im Array nicht verarbeiten

Dieser Artikel bietet eine Lösung für das Problem, dass die Web-API eine Nachricht, die mehr als 20 Elemente im Array für Adobe Commerce 2.4.3 enthält, nicht verarbeiten kann.

## Betroffene Produkte und Versionen:

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und 2.3.7-p1
* Magento Open Source 2.4.3 und 2.3.7-p1

## Problem

Die Web-API kann die Meldung (z. B. &quot;Stock Update&quot;), die mehr als 20 Elemente im Array enthält, nicht verarbeiten.

## Ursache

In Adobe Commerce 2.4.3 wurde die integrierte Ratenbegrenzung zu Magento-APIs hinzugefügt, um DoS-Angriffe (Denial-of-Service) zu verhindern.

Standardmäßig ist die folgende integrierte API-Ratenbegrenzung verfügbar:

* REST-Anfragen, die Eingaben enthalten, die eine Liste von Entitäten darstellen, sind auf eine Standardanzahl von 20 Entitäten beschränkt
* REST- und GraphQL-Abfragen, die paginierte Ergebnisse ermöglichen, sind auf eine Standardgrenze von 300 Elementen pro Seite beschränkt

## Lösung

Um die Eingabegrenzen für die REST-API-Anfrage zu deaktivieren, wenden Sie einen der folgenden Patches an (je nach Version):

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### Kompatible Adobe Commerce-Versionen

Die Patches wurden für Folgendes erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.4.3 und 2.3.7-p1
* Adobe Commerce vor Ort 2.4.3 und 2.3.7-p1

Die Patches sind nicht mit anderen Adobe Commerce-Versionen kompatibel.

### Anwenden des Pflasters

Entpacken Sie die heruntergeladene `.zip`-Datei und wenden Sie den Patch wie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches beschrieben an.

>[!WARNING]
>
>Wenn Sie vermuten, dass Ihr Store einen DoS-Angriff erfährt, empfiehlt Adobe, die Standardeingabeschränkungen auf einen niedrigeren Wert zu senken, um die Anzahl der Ressourcen, die angefordert werden können, zu beschränken.  Sie können die Standardbeschränkungen programmgesteuert mithilfe von [class -Konstruktorargumenten](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html) anpassen
>wie in unserer Entwicklerdokumentation beschrieben: [API-Sicherheit > Ratenbegrenzung > Maximale Parametereingaben](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## Verwandtes Lesen

[API-Sicherheit > Ratenbegrenzung](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting) in unserer Entwicklerdokumentation.
