---
title: Dringende Maßnahmen erforderlich Wichtiges Sicherheitsupdate für Adobe Commerce verfügbar (APSB26-146)
description: Adobe hat das Sicherheitsbulletin APSB26-146 veröffentlicht, das CVE-2026-75650 adressiert, eine Zero-Day-Schwachstelle in Adobe Commerce. Erfahren Sie, wie Sie den Hotfix anwenden und Anmeldeinformationen rotieren.
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 7526f999381e9f117ea2d52dc59330b0d34cba62
workflow-type: tm+mt
source-wordcount: 952
ht-degree: 0%

---


# Dringende Maßnahmen erforderlich: Wichtiges Sicherheitsupdate für Adobe Commerce verfügbar (APSB26-146)

>[!IMPORTANT]
>
>Dies ist eine dringende Aktualisierung im Zusammenhang mit CVE-2026-75650. Adobe ist sich bewusst, dass CVE-2026-75650 beim wilden Targeting von Adobe Commerce-Händlern ausgenutzt wurde.

Am 7. September veröffentlichte Adobe ein wichtiges Sicherheitsupdate, das Adobe Commerce und Magento Open Source betraf. Adobe wurde auf eine Zero-Day-Sicherheitslücke in Adobe Commerce aufmerksam und hat ein Sicherheitsupdate (APSB26-146) veröffentlicht, um diese zu beheben. Die Sicherheitslücke könnte es einem nicht authentifizierten Angreifer ermöglichen, beliebigen Code auf einer betroffenen Installation auszuführen (CVE-2026-75650).

Adobe hat das Sicherheitsbulletin APSB26-146 veröffentlicht, das diese Sicherheitslücke behebt. Das Bulletin finden Sie hier:

[Sicherheitsupdate für Adobe Commerce verfügbar | APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

In diesem Artikel wird erläutert, wie Sie den Hotfix für aktuelle und frühere Versionen von Adobe Commerce und Magento Open Source anwenden.

## Beschreibung

Betroffene Produkte und Versionen:

Adobe Commerce-Versionen:

* 2.4.9-2026-Aug und früher
* 2.4.8-2026-Aug und früher
* 2.4.7-2026-Aug und früher
* 2.4.6-2026-Aug und früher
* 2.4.5-2026-Aug und früher
* 2.4.4-2026-Aug und früher

Adobe Commerce B2B-Versionen:

* 1.5.3-2026-Aug und früher
* 1.5.2-2026-Aug und früher
* 1.4.2-2026-Aug und früher
* 1.3.4-2026-Aug und früher
* 1.3.3-2026-Aug und früher

Magento Open Source-Versionen:

* 2.4.9-2026-Aug und früher
* 2.4.8-2026-Aug und früher
* 2.4.7-2026-Aug und früher
* 2.4.6-2026-Aug und früher

## Auflösung

### Lösung für Adobe Commerce on Cloud, Adobe Commerce On-Premise und Magento Open Source

>[!NOTE]
>
>Das Hotfix für CVE-2026-75650 ist jetzt mit allen Versionen von Adobe Commerce und Magento Open Source zwischen 2.4.4 und 2.4.7 kompatibel. Bitte sehen Sie in der unten stehenden Tabelle nach, und laden Sie den Patch herunter, der für Ihre Version gilt.

Um die Sicherheitslücke für die betroffenen Produkte und Versionen zu beheben, müssen Sie den **unten stehenden Patch** anwenden (abhängig von Ihrer Version) und Ihre Verschlüsselungsschlüssel rotieren.

| Versionsnummer | Fleck |
|---|---|
| 2.4.9-2026-aug, 2.4.8-2026-aug, 2.4.7-2026-aug, 2.4.6-2026-aug, 2.4.5-2026-aug, 2.4.4-2026-aug, 2.4.9-2026-jul, 2.4.8-2026-jul, 2.4.7-2026-jul, 2.4.6-2026-jul, 2.4.5-2026-jul, 2.4.4-2026-jul, 2.4.8-p5, 2.4.8-p4, 2.4.7-p10, 2.4.7-p9, 2.4.6-p15, 2.4.6-p14, 2.4.5-p17, 2.4.5-p 2.4.4-p18, 2.4.4-p17 | [Hotfix VULN-39341-composer-patches.zip](https://repo.magento.com/patch/VULN-39341-composer-patches.zip) |
| 2.4.8-p3, 2.4.8-p2 | [VULN-39341_248-p3.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p3-patch.zip) |
| 2.4.8-p1, 2.4.8 | [VULN-39341_248-p1.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p1-patch.zip) |
| 2.4.7-p8, 2.4.7-p7 | [VULN-39341_247-p8.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p8-patch.zip) |
| 2.4.7 - 2.4.7-p6 | [VULN-39341_247-p5.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p5-patch.zip) |
| 2.4.6-p13, 2.4.6-p12, 2.4.5-p15, 2.4.5-p14, 2.4.4-p16, 2.4.4-p15 | [VULN-39341_246-p13.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p13-patch.zip) |
| 2.4.6 - 2.4.6-p11, 2.4.5 - 2.4.5-p13, 2.4.4 - 2.4.4-p14 | [VULN-39341_246-p11.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p11-patch.zip) |


{style="table-layout:auto"}

### Anwenden des Hotfixes

Entpacken Sie die Datei und [&#x200B; Sie in unserer Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)Wissensdatenbank die Anleitung „So wenden Sie einen von Adobe bereitgestellten Composer-Patch an“.

### Bestätigen der Anwendung des Hotfixes (nur Adobe Commerce auf Cloud-Händler)

Da nicht einfach festgestellt werden kann, ob das Problem behoben wurde, wird empfohlen zu überprüfen, ob der Hotfix CVE-2026-75650 erfolgreich angewendet wurde.

Dies können Sie tun, indem Sie die folgenden Schritte ausführen und dabei die Datei `VULN-39341_Hotfix_COMPOSER.patch` als Beispiel verwenden:

1. [Installieren Sie das Quality Patches Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage#install).
1. Führen Sie den Befehl `vendor/bin/magento-patches -n status | grep "39341\|Status"` aus.
1. Es sollte eine ähnliche Ausgabe angezeigt werden, bei der dieses Beispiel-VULN-39341 den Status Angewendet zurückgibt:

| ID | Titel | Kategorie | Entstehung | Status | Detail |
|---|---|---|---|---|---|
| Nicht zutreffend | …/m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | Sonstige | Lokal | Angewendet | Patch-Typ: Benutzerdefiniert |

### Drehen der Anmeldeinformationen nach der Anwendung des Patches

Um dieses Problem vollständig zu beheben, rotieren Sie nicht nur Ihren Verschlüsselungsschlüssel, sondern alle Anmeldeinformationen, die damit verschlüsselt oder bereitgestellt wurden, einschließlich Server-, API- und Integrations-Anmeldeinformationen.

>[!NOTE]
>
>Der Verschlüsselungsschlüssel wird verwendet, um Integrations-Token, Anmeldedaten für das Zahlungs-Gateway und systemprivilegierte Automatisierungs-Token zu verschlüsseln. Durch Drehen des Verschlüsselungsschlüssels allein werden Anmeldeinformationen, die möglicherweise bereits offen gelegt wurden, nicht ungültig gemacht. Rotieren Sie alle zugehörigen Anmeldeinformationen an ihrer Quelle (z. B. am Zahlungs-Gateway oder bei Diensten von Drittanbietern), nicht nur innerhalb von Commerce.

Gehen Sie wie folgt vor, um Anmeldeinformationen zu rotieren:

1. Wenden Sie den Hotfix an.
1. Wartungsmodus aktivieren.
1. Deaktivieren Sie die Cron-Ausführung (Commerce in Cloud-Befehl: `vendor/bin/ece-tools cron:disable`).
1. [Drehen Sie Ihre Verschlüsselungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key?lang=en).
1. Rotieren Sie alle Administratorbereich-Benutzerkennwörter.
1. Deaktivieren und regenerieren Sie alle REST/SOAP/GraphQL-Integrations-Token (**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**).
1. Rotieren von OAuth-Client-Geheimnissen für alle verbundenen Anwendungen von Drittanbietern.
1. Rotieren der Anmeldedaten für die Payment Gateway-API auf Anbieterebene (Stripe, Braintree, Adyen, PayPal usw.)
1. Rotieren von Datenbankanmeldeinformationen.
1. Rotieren/Bereitstellen von SSH-Schlüsseln und Anmeldeinformationen für Cron- oder systemberechtigte Service-Konten.
1. Rotieren von API-Schlüsseln für Versand, Steuern und andere integrierte Erweiterungen von Drittanbietern.
1. Leeren Sie den Cache.
1. Aktivieren der Cron-Ausführung (Commerce in Cloud-Befehl: `vendor/bin/ece-tools cron:enable`).
1. Deaktivieren Sie den Wartungsmodus.
1. Nur Commerce in Cloud: Neu bereitstellen, um neue Datenbankanmeldeinformationen anzuwenden.

### Sicherheits-Updates

Für Adobe Commerce verfügbare Sicherheitsupdates:

* [Adobe-Sicherheitsbulletin (APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [Die neuesten für Adobe Commerce verfügbaren Sicherheitsupdates](https://helpx.adobe.com/security/products/magento.html)

### Verwandtes Lesen

[Aktivieren oder Deaktivieren des &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en) im Adobe Commerce-Installationshandbuch
