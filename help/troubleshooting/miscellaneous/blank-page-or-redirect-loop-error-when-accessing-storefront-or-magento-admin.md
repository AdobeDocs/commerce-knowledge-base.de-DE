---
title: Fehler wegen leerer Seite oder Umleitungsschleife beim Zugriff auf Storefront oder Commerce Admin
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie auf die Adobe Commerce-Storefront oder das Backend zugreifen und eine leere Seite oder Umleitungsschleife erhalten.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Fehler wegen leerer Seite oder Umleitungsschleife beim Zugriff auf Storefront oder Commerce Admin

Dieser Artikel bietet eine Lösung für das Problem, wenn Sie auf die Adobe Commerce-Storefront oder das Backend zugreifen und eine leere Seite oder Umleitungsschleife erhalten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen
* Adobe Commerce On-Premise, alle Versionen
* Magento Open Source, alle Versionen

## Problem

<u>Schritte zur Reproduktion</u>

Öffnen Sie eine Storefront oder Admin-Seite.

<u>Erwartetes Ergebnis</u>

Die Seite wird geöffnet.

<u>Tatsächliches Ergebnis</u>

Die Seite ist leer oder zeigt die Fehlermeldung *Diese Webseite hat eine Umleitungsschleife* an.

## Ursache

Einer der wahrscheinlichsten Gründe für das Problem ist, dass Adobe Commerce so eingestellt ist, dass es von einer unsicheren URL zu einer sicheren URL umleitet, aber eine unsichere URL als Wert für die Einstellung der sicheren URL angegeben wird.

Um das Problem zu beheben, müssen Sie den Wert des sicheren Links korrigieren.

## Lösung

Um sicherzustellen, dass dies die Ursache des Problems ist, führen Sie die folgenden Schritte aus:

1. Überprüfen Sie den Wert `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (wenn Sie das Problem „leer/Schleifenumleitung“ in Admin haben) oder `web/secure/use_in_frontend` (wenn Sie das Problem „leer/Schleifenumleitung“ in der Storefront haben) in der Tabelle `'core_config_data'` DB.
   * Wenn `web/secure/enable_upgrade_insecure` auf „1“ festgelegt ist, wird Adobe Commerce eingerichtet, um die Antwort-Header-`Content-Security-Policy: upgrade-insecure-requests` hinzuzufügen, sodass Browser HTTPS verwenden und alle Abfragen, die über HTTP erfolgen, umleiten
in HTTPS, sowohl für Admin als auch für Storefront.
   * Wenn `web/secure/use_in_adminhtml` auf „1“ eingestellt ist, gibt Adobe Commerce HTTPS-Umleitungen für alle HTTP-Anfragen für die Admin-Seiten zurück.
   * Wenn `web/secure/use_in_frontend` auf „1“ gesetzt ist, gibt Adobe Commerce HTTPS-Umleitungen für alle HTTP-Anfragen für die Store-Frontseiten zurück.
1. Überprüfen Sie die `web/secure/base_url`- und `web/unsecure/base_url` in der `'core_config_data'`. Wenn beide beginnen mit    `http` müssen Sie dann den Wert „sicher“ korrigieren.

Beheben des Problems:

1. Wert festlegen, der mit `https` für `web/secure/base_url.` beginnt
1. Damit die Änderungen angewendet werden, bereinigen Sie den Konfigurations-Cache, indem Sie den folgenden Befehl ausführen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
