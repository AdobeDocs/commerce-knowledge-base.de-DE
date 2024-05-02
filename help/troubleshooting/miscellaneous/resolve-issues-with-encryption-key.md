---
title: Beheben von Problemen mit dem Verschlüsselungsschlüssel
description: In diesem Artikel wird beschrieben, wie Sie die Probleme beheben, die durch den Verschlüsselungsschlüssel verursacht werden, der nicht zusammen mit dem DB-Dump in die andere Umgebung verschoben wird.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: bee0263da487399ab07bf9158c4d60ab316d6ea1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Beheben von Problemen mit dem Verschlüsselungsschlüssel

In diesem Artikel wird beschrieben, wie Sie die Probleme beheben, die durch den Verschlüsselungsschlüssel verursacht werden, der nicht zusammen mit dem DB-Dump in die andere Umgebung verschoben wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Nach dem Import einer [Datenbank-Dump](/help/how-to/general/create-database-dump-on-cloud.md) von der Produktions- zur Staging-/Integrationsumgebung, erscheinen gespeicherte Kreditkartennummern falsch und/oder Zahlungen schlagen bei Zahlungsintegrationen fehl, die die Verwendung von Händleranmeldeinformationen erfordern.

## Ursache

Der Verschlüsselungsschlüssel, der zum Verschlüsseln sensibler Daten wie Kreditkartennummern und Händleranmeldeinformationen verwendet wird, wird nicht in der Datenbank gespeichert und wird daher nach dem Import/Export der Datenbank-Dump nicht in andere Umgebungen übertragen.

## Lösung

Sie müssen den Verschlüsselungsschlüssel aus der Quellumgebung kopieren und in die Zielumgebung einfügen.

So kopieren Sie den Verschlüsselungsschlüssel:

1. SSH zu Ihrem Projekt, das die Quelle für die Datenbank-Dump war, wie beschrieben in [SSH in der Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in unserer Entwicklerdokumentation.
1. Öffnen `app/etc/env.php` in einem Texteditor.
1. Den Wert von `key` für `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

So legen Sie den Schlüsselwert für das Zielprojekt fest:

1. Öffnen Sie die [Cloud-Konsole](https://console.adobecommerce.com) und suchen Sie Ihr Projekt.
1. Legen Sie den Wert der [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (in unserer Entwicklerdokumentation), wie hier beschrieben: [Projekt konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) in unserer Entwicklerdokumentation. Dadurch wird der Bereitstellungsprozess Trigger und `CRYPT_KEY` wird im `app/etc/env.php` -Datei bei jeder Bereitstellung.

Optional können Sie den Verschlüsselungsschlüssel im `app/etc/env.php` Datei:

1. SSH in die Zielumgebung.
1. Öffnen `app/etc/env.php` in einem Texteditor.
1. Fügen Sie die kopierten Daten als `key` Wert für `crypt`.
1. Speichern Sie die bearbeitete `env.php`.
1. Cache in der Zielumgebung bereinigen, indem Sie `bin/magento cache:clean` oder im Commerce Admin unter **System** > **Instrumente** > **Cacheverwaltung**.
