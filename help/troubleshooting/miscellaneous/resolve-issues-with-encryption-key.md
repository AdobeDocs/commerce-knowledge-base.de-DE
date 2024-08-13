---
title: Beheben von Problemen mit dem Verschlüsselungsschlüssel
description: In diesem Artikel wird beschrieben, wie Sie die Probleme beheben, die durch den Verschlüsselungsschlüssel verursacht werden, der nicht zusammen mit dem DB-Dump in die andere Umgebung verschoben wird.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Beheben von Problemen mit dem Verschlüsselungsschlüssel

In diesem Artikel wird beschrieben, wie Sie die Probleme beheben, die durch den Verschlüsselungsschlüssel verursacht werden, der nicht zusammen mit dem DB-Dump in die andere Umgebung verschoben wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.x

## Problem

Nach dem Import eines [Datenbank-Dump](/help/how-to/general/create-database-dump-on-cloud.md) aus der Produktions- in Staging-/Integrationsumgebung erscheinen gespeicherte Kreditkartennummern falsch und/oder Zahlungen schlagen bei Zahlungsintegrationen fehl, die die Verwendung von Händleranmeldeinformationen erfordern.

## Ursache

Der Verschlüsselungsschlüssel, der zum Verschlüsseln sensibler Daten wie Kreditkartennummern und Händleranmeldeinformationen verwendet wird, wird nicht in der Datenbank gespeichert und wird daher nach dem Import/Export der Datenbank-Dump nicht in andere Umgebungen übertragen.

## Lösung

Sie müssen den Verschlüsselungsschlüssel aus der Quellumgebung kopieren und in die Zielumgebung einfügen.

So kopieren Sie den Verschlüsselungsschlüssel:

1. SSH zu Ihrem Projekt, das die Quelle für die Datenbank-Dump war, wie in der Entwicklerdokumentation unter [SSH in die Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) beschrieben.
1. Öffnen Sie `app/etc/env.php` in einem Texteditor.
1. Kopieren Sie den Wert von `key` für `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

So legen Sie den Schlüsselwert für das Zielprojekt fest:

1. Öffnen Sie die [Cloud-Konsole](https://console.adobecommerce.com) und suchen Sie Ihr Projekt.
1. Legen Sie den Wert der Variablen [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (in unserer Entwicklerdokumentation) fest, wie in der Entwicklerdokumentation unter [Konfigurieren Sie Ihr Projekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) beschrieben. Dadurch wird der Bereitstellungsprozess Trigger und `CRYPT_KEY` wird bei jeder Bereitstellung in der `app/etc/env.php` -Datei überschrieben.

Optional können Sie den Verschlüsselungsschlüssel in der Datei `app/etc/env.php` manuell überschreiben:

1. SSH in die Zielumgebung.
1. Öffnen Sie `app/etc/env.php` in einem Texteditor.
1. Fügen Sie die kopierten Daten als `key` -Wert für `crypt` ein.
1. Speichern Sie die bearbeitete `env.php`.
1. Bereinigen Sie den Cache in der Zielumgebung, indem Sie `bin/magento cache:clean` oder im Commerce Admin unter **System** > **Tools** > **Cache-Verwaltung** ausführen.
