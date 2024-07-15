---
title: .magento.env.yaml-Änderungen, die nach der Bereitstellung nicht in env.php angezeigt werden
description: Dieser Artikel bietet eine Lösung für das Problem, dass Änderungen in der .magento.env.yaml-Datei nach der Bereitstellung nicht in app/etc/env.php angezeigt werden.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml-Änderungen, die nach der Bereitstellung nicht in env.php angezeigt werden

>[!NOTE]
>
>Wenn Sie dieses Problem haben, aktualisieren Sie auf ece-tools 2002.1.5, um es zu beheben. 2002.1.5 verfügt über Funktionen zum Zurücksetzen des opcache bei jeder Bereitstellung, sodass die Einstellung `opcache.enable_cli=1` nie geändert werden muss. Wenn Sie kein Upgrade durchführen möchten, müssen Sie die Problemumgehungsschritte ausführen, wie unten in der Lösung beschrieben.

Dieser Artikel bietet eine Lösung für das Problem, dass Änderungen in der `.magento.env.yaml` -Datei nicht in `app/etc/env.php` nach der Bereitstellung angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur (alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problem

Änderungen, die in der Datei `.magento.env.yaml` vorgenommen wurden, wirken sich nicht auf den generierten `app/etc/env.php` aus.

<u>Zu reproduzierende Schritte:</u>

Ändern Sie einen beliebigen Wert in `.magento.env.yaml` und pushen Sie ihn auf den Server, wo er die Konfiguration (und Bereitstellungseinstellungen) für die derzeit ausgecheckte Umgebung definieren sollte. Anweisungen finden Sie unter [Umgebungsvariablen > Variablen bereitstellen](https://devdocs.magento.com/cloud/env/variables-deploy.html) in unserer Entwicklerdokumentation.

<u>Erwartetes Ergebnis:</u>

Änderungen, die in der Datei `.magento.env.yaml` vorgenommen werden, wirken sich auf den generierten `app/etc/env.php` aus.

<u>Tatsächliches Ergebnis:</u>

Die Änderungen wirken sich nicht auf die `app/etc/env.php` -Variablen nach der Bereitstellung aus.

## Ursache

Das Problem kann durch den falschen Wert des Parameters `opcache.enable_cli` in der Datei `php.ini` verursacht werden.

## Lösung

1. Vergewissern Sie sich, dass das System gemäß [Best Practices zur Adobe Commerce-Leistung > Softwareempfehlungen](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html) konfiguriert ist.
1. Überprüfen Sie, ob die Anweisung `opcache.enable_cli` in `php.ini` auf `0` gesetzt ist, indem Sie Folgendes ausführen: `php -i | grep opcache.enable_cli`
1. Wenn die Ausgabe wie `opcache.enable_cli=1` aussieht, bearbeiten Sie die Datei `php.ini` im Projektstammverzeichnis und ändern Sie `opcache.enable_cli=1` in `opcache.enable_cli=0`
1. Stellen Sie das Projekt erneut bereit.

## Verwandtes Lesen

* [Cloud für Adobe Commerce > Erstellen und Bereitstellen](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
