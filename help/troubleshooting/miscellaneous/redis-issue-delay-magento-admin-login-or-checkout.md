---
title: Wiederholungsproblem verzögert Commerce Admin-Anmeldung oder Checkout
description: In diesem Artikel wird das Problem behoben, das bei der Anmeldung beim Commerce-Administrator oder beim Öffnen der Checkout-Seite zu Verzögerungen oder Zeitüberschreitungen (über 30 Sekunden) führt. Das Problem tritt auf, wenn Redis für die Sitzungsspeicherung verwendet wird.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Wiederholungsproblem verzögert Commerce Admin-Anmeldung oder Checkout

In diesem Artikel wird das Problem behoben, das bei der Anmeldung beim Commerce-Administrator oder beim Öffnen der Checkout-Seite zu Verzögerungen oder Zeitüberschreitungen (über 30 Sekunden) führt. Das Problem tritt auf, wenn Redis für die Sitzungsspeicherung verwendet wird.

**Ursache:**   [GitHub-Problem \#12385](https://github.com/magento/magento2/issues/12385).

**Lösung:** Aktualisieren Sie auf den neuesten Adobe Commerce-Patch, um diese Probleme für alle Versionen von Redis und bestimmte Versionen von Adobe Commerce zu beheben.

## Betroffene Versionen und Technologien

* Adobe Commerce auf Cloud-Infrastrukturversionen 2.1.11 - 2.1.13 und 2.2.1
* Vor-Ort-Versionen von Adobe Commerce 2.1.11 - 2.1.13 und 2.2.1
* Redis, alle Versionen

Wenn Sie Adobe Commerce in der Cloud-Infrastrukturversion [2.2.0](#h_64593789291526919876198) verwenden, ist eine Problemumgehung verfügbar.

## Problem

Die Anmeldung beim Commerce-Administrator oder das Fortfahren mit der Checkout-Seite dauert über 30 Sekunden.

Dies tritt nur auf, wenn Benutzersitzungen in Redis gespeichert werden.

## Ursache

Adobe Commerce hatte ein Problem mit dem Sitzungssperrmechanismus, durch den einigen Vorgängen ein 30-Sekunden-Timeout hinzugefügt wurde, wenn Redis für die Sitzungsspeicherung verwendet wurde. Weitere Informationen finden Sie unter [GitHub-Problem \#12385](https://github.com/magento/magento2/issues/12385).

Dieses Problem wurde in Adobe Commerce 2.1.14 und 2.2.2 behoben.

## Lösungen: Patch oder Upgrade

### Lösung 1: Wenden Sie den Patch mit einem Fix an

Um einen Patch zu erhalten, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), das den Patch anfordert. Geben Sie in Ihrem Ticket Ihre Adobe Commerce-Version und die entsprechende Referenznummer für den Patch an:

* **2.1.11 und höher:** MDVA-7835
* **2.2.1:** MDVA-8128

Die allgemeine (versionsunabhängige) Referenznummer ist MAGETWO-84289.

### Lösung 2: Upgrade auf 2.1.14/2.2.2 oder höher

Wenn Sie bereits ein Upgrade auf Adobe Commerce 2.2.2 oder höher in Erwägung gezogen haben, können Sie diese Aktualisierungsmöglichkeit nutzen, um das Problem zu beheben.

## Problemumgehung: Sitzungssperrung deaktivieren

Um die Sitzungssperrung zu deaktivieren, setzen Sie `disable_locking` im Abschnitt &quot;Redis configuration&quot;der Datei `env.php` auf `1`:

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

Diese Lösung wirkt sich nicht auf andere Adobe Commerce-Funktionen aus.

### Behelfslösung nach Anwenden des Pflasters wiederherstellen

Nachdem Sie den Patch mit der Korrektur angewendet haben, ist die Problemumgehung nicht mehr erforderlich, sodass Sie ihn zurücksetzen können (setzen Sie `disable_locking` auf `0`).

## Adobe Commerce auf Cloud-Infrastruktur 2.2.0: ECE-Tools v2002.0.8 oder höher verwenden {#h_64593789291526919876198}

Das Bereitstellungsskript-Paket [ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) mit den Versionen 2002.0.3 - 2002.0.7 [wendet ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) die Problemumgehung automatisch an und legt `disable_locking` auf `1` fest. Dadurch wird der Sitzungssperrmechanismus für Adobe Commerce 2.2.0 deaktiviert, bei dem das ursprüngliche Problem nicht auftritt.

Wenn Sie Adobe Commerce in der Cloud-Infrastruktur 2.2.0 ausführen, aktualisieren Sie ECE-Tools auf Version 2002.0.8 von höher. Sie können auch erwägen, Ihre Adobe Commerce in der Cloud-Infrastruktur auf 2.2.2 oder höher zu aktualisieren.
