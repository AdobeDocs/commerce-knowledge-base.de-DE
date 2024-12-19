---
title: .magento.env.yaml Änderungen werden in env.php nach der Bereitstellung nicht angezeigt
description: Dieser Artikel bietet eine Lösung für das Problem, dass Änderungen in der Datei ".magento.env.yaml“ nach der Bereitstellung nicht in app/etc/env.php widergespiegelt werden.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml Änderungen werden in env.php nach der Bereitstellung nicht angezeigt

>[!NOTE]
>
>Wenn Sie dieses Problem haben, aktualisieren Sie auf ECE-Tools 2002.1.5, um es zu beheben. 2002.1.5 verfügt über Funktionen zum Zurücksetzen des OpCache bei jeder Bereitstellung, sodass es nie erforderlich ist, die `opcache.enable_cli=1` zu ändern. Wenn Sie kein Upgrade durchführen möchten, müssen Sie die Problemumgehungsschritte wie unten in der Lösung beschrieben durchführen.

Dieser Artikel bietet eine Lösung für das Problem, dass Änderungen in `.magento.env.yaml` Datei nach der Bereitstellung nicht in `app/etc/env.php` widergespiegelt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf))

## Problem

Änderungen an der `.magento.env.yaml`-Datei wirken sich nicht auf die generierte `app/etc/env.php` aus.

<u>Schritte zur Reproduktion:</u>

Ändern Sie einen beliebigen Wert in `.magento.env.yaml` und übertragen Sie ihn auf den -Server, wo er die Konfiguration (und die Bereitstellungseinstellungen) für die aktuell ausgecheckte Umgebung definieren soll. Anweisungen hierzu finden Sie [Umgebungsvariablen > Variablen bereitstellen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy) in unserer Entwicklerdokumentation.

<u>Erwartetes Ergebnis:</u>

Änderungen an der `.magento.env.yaml` wirken sich auf die generierten `app/etc/env.php` aus.

<u>Tatsächliches Ergebnis:</u>

Die Änderungen wirken sich nach der Bereitstellung nicht auf die `app/etc/env.php` aus.

## Ursache

Das Problem kann durch den falschen Wert des `opcache.enable_cli`-Parameters in der `php.ini`-Datei verursacht werden.

## Lösung

1. Vergewissern Sie sich, dass das System gemäß den [Best Practices für die Adobe Commerce-Leistung > Softwareempfehlungen konfiguriert ](https://experienceleague.adobe.com/en/docs/commerce-operations/performance-best-practices/software).
1. Überprüfen Sie, ob `opcache.enable_cli` -Anweisung in `php.ini` auf `0` festgelegt ist, indem Sie Folgendes ausführen: `php -i | grep opcache.enable_cli`
1. Wenn die Ausgabe wie `opcache.enable_cli=1` aussieht, bearbeiten Sie die `php.ini` im Stammverzeichnis des Projekts und ändern Sie `opcache.enable_cli=1` in `opcache.enable_cli=0`
1. Stellen Sie das Projekt erneut bereit.

## Verwandtes Lesen

* [Cloud für Adobe Commerce > Erstellen und bereitstellen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml).
