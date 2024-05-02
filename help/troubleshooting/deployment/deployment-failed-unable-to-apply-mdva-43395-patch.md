---
title: "Freigabe fehlgeschlagen: MDVA-43395-Patch kann nicht angewendet werden"
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem der Versuch, den MDVA-43395-Patch anzuwenden, zu einer fehlgeschlagenen Implementierung führt.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Freigabe fehlgeschlagen: MDVA-43395-Patch kann nicht angewendet werden

Dieser Artikel bietet eine Lösung für das Problem, bei dem der Versuch, den MDVA-43395-Patch anzuwenden, zu einer fehlgeschlagenen Implementierung führt.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

Sie können den Patch MDVA-43395 nicht anwenden.

## Ursache

Cloud-Händler müssen den MDVA-43395-Patch nicht separat anwenden, wenn sie [magento/magento-cloud-patches 1.0.16](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) installiert, die bereits den Patch enthält.

## Lösung

Um das Problem zu beheben, entfernen Sie die MDVA-43395- und MDVA-43443-Pflaster aus dem `m2-hotfixes` Verzeichnis erstellen und erneut bereitstellen.

Wenn Sie das MDVA-43443 Pflaster über die `m2-hotfixes` -Verzeichnis, müssen Sie es dennoch entfernen, wie oben erwähnt. In zukünftigen Versionen von Adobe Commerce sind diese Patches bereits enthalten, sodass die Bereitstellung fehlschlagen könnte, wenn Sie später aktualisieren würden.

Um zu überprüfen, ob der Patch angewendet wurde, führen Sie den `vendor/bin/magento-patches -n status |grep 43443` Befehl.
Wenn es mehrere Ergebnisse wie diese zeigt, sollten Sie den MDVA-43443 Patch aus dem `m2-hotfixes` Ordner:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Verwandtes Lesen

* [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Wissensdatenbank.
* [Cloud-Patches für Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) in unserer Entwicklerdokumentation.
