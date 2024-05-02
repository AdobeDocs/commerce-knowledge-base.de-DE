---
title: Fehler bei leerem Seiten- oder Umleitungs-Loop beim Zugriff auf Storefront oder Commerce Admin
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie auf Adobe Commerce Storefront oder Backend zugreifen und eine leere Seite oder Umleitungsschleife erhalten.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Fehler bei leerem Seiten- oder Umleitungs-Loop beim Zugriff auf Storefront oder Commerce Admin

Dieser Artikel bietet eine Lösung für das Problem, wenn Sie auf Adobe Commerce Storefront oder Backend zugreifen und eine leere Seite oder Umleitungsschleife erhalten.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen
* Adobe Commerce vor Ort, alle Versionen
* Magento Open Source, alle Versionen

## Problem

<u>Zu reproduzierende Schritte</u>

Öffnen Sie eine Storefront oder Admin-Seite.

<u>Erwartetes Ergebnis</u>

Die Seite wird geöffnet.

<u>Tatsächliches Ergebnis</u>

Die Seite ist leer oder zeigt die *&quot;Diese Webseite hat eine Umleitungsschleife&quot;* Fehlermeldung.

## Ursache

Einer der wahrscheinlichsten Gründe für das Problem ist, dass Adobe Commerce von einer unsicheren URL zu einer sicheren URL umgeleitet wird, aber eine unsichere URL als Wert für die sichere URL-Einstellung angegeben wird.

Um das Problem zu beheben, müssen Sie den Wert des sicheren Links korrigieren.

## Lösung

Gehen Sie wie folgt vor, um sicherzustellen, dass dies die Ursache des Problems ist:

1. Überprüfen Sie die `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (wenn Sie in Admin ein Problem mit der Leer-/Schleifenumleitung haben) oder `web/secure/use_in_frontend` (wenn Sie das Leer-/Schleifenumleitungsproblem auf der Storefront haben) im Wert `'core_config_data'` DB-Tabelle.
   * Wenn `web/secure/enable_upgrade_insecure` auf &quot;1&quot;festgelegt ist, wird Adobe Commerce so eingerichtet, dass der Antwortheader hinzugefügt wird. `Content-Security-Policy: upgrade-insecure-requests`, wodurch Browser angewiesen werden, HTTPS zu verwenden, und alle Abfragen, die über HTTP erfolgen, sowohl für Admin als auch für Storefront an HTTPS umgeleitet werden.
   * Wenn `web/secure/use_in_adminhtml` auf &quot;1&quot;festgelegt ist, gibt Adobe Commerce HTTPS-Umleitungen für alle HTTP-Anforderungen für die Admin-Seiten zurück.
   * Wenn `web/secure/use_in_frontend` auf &quot;1&quot;festgelegt ist, gibt Adobe Commerce HTTPS-Umleitungen für alle HTTP-Anforderungen für die Store-Titelseiten zurück.
1. Überprüfen Sie die `web/secure/base_url` und `web/unsecure/base_url` -Werte in `'core_config_data'` Tabelle. Wenn beide mit    `http`, müssen Sie den Wert &quot;secure&quot;korrigieren.

Behebung des Problems:

1. Festlegen des Werts, der mit `https` für `web/secure/base_url.`
1. Um die Änderungen anzuwenden, leeren Sie den Konfigurationscache, indem Sie den folgenden Befehl ausführen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
