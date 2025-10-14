---
title: Problemverzögerung bei Commerce-Admin-Anmeldung oder -Checkout beheben
description: Dieser Artikel bietet eine Lösung für das Problem, dass beim Anmelden bei Commerce Admin oder beim Öffnen der Checkout-Seite zu Verzögerungen oder Zeitüberschreitungen (über 30 Sekunden) führt. Das Problem tritt auf, wenn Redis als Sitzungsspeicher verwendet wird.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Problemverzögerung bei Commerce-Admin-Anmeldung oder -Checkout beheben

Dieser Artikel bietet eine Lösung für das Problem, dass beim Anmelden bei Commerce Admin oder beim Öffnen der Checkout-Seite zu Verzögerungen oder Zeitüberschreitungen (über 30 Sekunden) führt. Das Problem tritt auf, wenn Redis als Sitzungsspeicher verwendet wird.

**Ursache:**   [GitHub-Problem \#12385](https://github.com/magento/magento2/issues/12385).

**Lösung:** Aktualisieren Sie auf den neuesten Adobe Commerce-Patch, um diese Probleme für alle Versionen von Redis und bestimmte Versionen von Adobe Commerce zu beheben.

## Betroffene Versionen und Technologien

* Adobe Commerce auf Cloud-Infrastruktur-Versionen 2.1.11 - 2.1.13 und 2.2.1
* Adobe Commerce On-Premise-Versionen 2.1.11 - 2.1.13 und 2.2.1
* Redis, alle Versionen

Wenn Sie Adobe Commerce in der Cloud-Infrastrukturversion [2.2.0](#h_64593789291526919876198) verwenden, ist eine Problemumgehung verfügbar.

## Problem

Die Anmeldung bei der Commerce-Administratorin bzw. dem-Administrator oder der Übergang zur Kaufbestätigungsseite dauert mehr als 30 Sekunden.

Dies tritt nur auf, wenn Benutzersitzungen in Redis gespeichert werden.

## Ursache

Adobe Commerce hatte ein Problem mit dem Sitzungssperrmechanismus, der bei einigen Vorgängen eine maximale Wartezeit von 30 Sekunden hinzufügte, wenn Redis für die Sitzungsspeicherung verwendet wurde. Weitere Informationen finden Sie unter [Github-Problem \#12385](https://github.com/magento/magento2/issues/12385).

Dieses Problem wurde in Adobe Commerce 2.1.14 und 2.2.2 behoben.

## Lösungen: Patch oder Upgrade

### Lösung 1: Wenden Sie das Pflaster mit einer Fehlerbehebung an

Um einen Patch zu erhalten[&#x200B; fordern Sie (ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) den Patch an. Geben Sie in Ihrem Ticket Ihre Adobe Commerce-Version und die entsprechende Referenznummer für den Patch an:

* **2.1.11 und höher:** MDVA-7835
* **2.2.1:** MDVA-8128

Die allgemeine (versionsunabhängige) Referenznummer ist MAGETWO-84289.

### Lösung 2: Upgrade auf 2.1.14/2.2.2 oder höher

Wenn Sie bereits ein Upgrade auf Adobe Commerce 2.2.2 oder höher in Betracht gezogen haben, können Sie diese Update-Gelegenheit nutzen, um das Problem zu beheben.

## Problemumgehung: Deaktivieren der Sitzungssperre

Um die Sitzungssperre zu deaktivieren, legen Sie `disable_locking` im Abschnitt Redis-Konfiguration der `env.php`-Datei auf `1` fest:

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

Diese Lösung hat keine Auswirkungen auf andere Adobe Commerce-Funktionen.

### Problemumgehung nach der Installation des Patches wiederherstellen

Nachdem Sie den Patch mit der Fehlerbehebung angewendet haben, ist die Problemumgehung nicht mehr erforderlich, sodass Sie sie möglicherweise zurücksetzen können (`disable_locking` auf `0` gesetzt).

## Adobe Commerce on Cloud Infrastructure 2.2.0: Verwenden Sie die ECE-Tools der Version 2002.0.8 oder höher. {#h_64593789291526919876198}

Das Bereitstellungsskriptpaket [ECE-Tools](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) mit den Versionen 2002.0.3 bis 2002.0.7 [gilt automatisch für &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=de) Problemumgehung, wobei `disable_locking` auf `1` gesetzt wird. Dadurch wird der Sitzungssperrmechanismus für Adobe Commerce 2.2.0 deaktiviert, bei dem das ursprüngliche Problem nicht auftritt.

Wenn Sie Adobe Commerce auf Cloud-Infrastruktur 2.2.0 ausführen, aktualisieren Sie ECE-Tools auf Version 2002.0.8 oder höher. Sie können auch erwägen, Ihre Adobe Commerce on Cloud-Infrastruktur auf Version 2.2.2 oder höher zu aktualisieren.
