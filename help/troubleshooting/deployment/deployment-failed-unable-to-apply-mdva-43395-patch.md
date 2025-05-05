---
title: 'Bereitstellung fehlgeschlagen: MDVA-43395-Patch kann nicht angewendet werden'
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem der Versuch, den MDVA-43395-Patch anzuwenden, zu einer fehlgeschlagenen Bereitstellung führt.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Bereitstellung fehlgeschlagen: MDVA-43395-Patch kann nicht angewendet werden

Dieser Artikel bietet eine Lösung für das Problem, bei dem der Versuch, den MDVA-43395-Patch anzuwenden, zu einer fehlgeschlagenen Bereitstellung führt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Problem

Sie können das MDVA-43395-Patch nicht anwenden.

## Ursache

Cloud-Händler müssen den MDVA-43395-Patch nicht separat anwenden, wenn sie [magento/magento-cloud-patches 1.0.16](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) installiert haben, die den Patch bereits enthalten.

## Lösung

Um das Problem zu beheben, entfernen Sie die MDVA-43395- und MDVA-43443-Patches aus dem `m2-hotfixes` und stellen Sie erneut bereit.

Wenn Sie den MDVA-43443 Patch über das `m2-hotfixes` Verzeichnis anwenden können, müssen Sie ihn dennoch wie oben beschrieben entfernen. In zukünftigen Versionen von Adobe Commerce sind diese Patches bereits enthalten. Daher kann es sein, dass die Bereitstellung fehlschlägt, wenn Sie später ein Upgrade durchführen.

Um zu überprüfen, ob der Patch angewendet wurde, führen Sie den `vendor/bin/magento-patches -n status |grep 43443` Befehl aus.
Wenn mehrere Ergebnisse wie diese angezeigt werden, sollten Sie den MDVA-43443-Patch aus dem `m2-hotfixes` Ordner entfernen:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Verwandtes Lesen

* [So wenden Sie einen Composer-Patch von Adobe an](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank.
* [Cloud-Patches für Commerce](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) in unserer Entwicklerdokumentation.
