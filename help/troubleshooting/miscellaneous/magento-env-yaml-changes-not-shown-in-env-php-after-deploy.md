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
>Wenn Sie dieses Problem haben, aktualisieren Sie auf ece-tools 2002.1.5, um es zu beheben. 2002.1.5 verfügt über Funktionen zum Zurücksetzen des opcache bei jeder Bereitstellung, sodass die Einstellung nie geändert werden muss `opcache.enable_cli=1`. Wenn Sie kein Upgrade durchführen möchten, müssen Sie die Problemumgehungsschritte ausführen, wie unten in der Lösung beschrieben.

Dieser Artikel bietet eine Lösung für das Problem, bei dem Änderungen in `.magento.env.yaml` -Datei nicht in `app/etc/env.php` nach der Bereitstellung.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problem

Änderungen, die im `.magento.env.yaml` hat keine Auswirkungen auf die `app/etc/env.php` generiert.

<u>Zu reproduzierende Schritte:</u>

Ändern Sie einen Wert in `.magento.env.yaml` und Push an den Server, wo die Konfiguration (und Bereitstellungseinstellungen) für die derzeit ausgecheckte Umgebung definiert werden sollte. Anweisungen finden Sie unter [Umgebungsvariablen > Variablen bereitstellen](https://devdocs.magento.com/cloud/env/variables-deploy.html) in unserer Entwicklerdokumentation.

<u>Erwartetes Ergebnis:</u>

Änderungen, die im `.magento.env.yaml` die Datei `app/etc/env.php` generiert.

<u>Ergebnis:</u>

Die Änderungen wirken sich nicht auf die `app/etc/env.php` Variablen nach der Bereitstellung.

## Ursache

Das Problem kann durch den falschen Wert der `opcache.enable_cli` -Parameter in der `php.ini` -Datei.

## Lösung

1. Überprüfen Sie, ob das System gemäß [Best Practices für die Leistung von Adobe Commerce > Softwareempfehlungen](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. Überprüfen Sie, ob `opcache.enable_cli` in `php.ini` auf `0` durch Ausführung: `php -i | grep opcache.enable_cli`
1. Wenn die Ausgabe wie folgt aussieht `opcache.enable_cli=1` , bearbeiten Sie die `php.ini` Datei im Stammverzeichnis des Projekts und ändern Sie `opcache.enable_cli=1` nach `opcache.enable_cli=0`
1. Stellen Sie das Projekt erneut bereit.

## Verwandtes Lesen

* [Cloud für Adobe Commerce > Erstellen und Bereitstellen](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
