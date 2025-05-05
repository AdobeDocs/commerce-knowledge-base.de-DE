---
title: '[!DNL B2B] 1.4.0-Installation schlägt auf Adobe Commerce 2.4.6-P1 On-Premise fehl'
description: Dieser Artikel bietet eine Problemumgehung für das On-Premise-Problem von Adobe Commerce 2.4.6-p1, bei dem die Installation  [!DNL B2B] Version 1.4.0 fehlschlägt.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# [!DNL B2B] 1.4.0-Installation schlägt auf Adobe Commerce 2.4.6-P1 On-Premise fehl

Dieser Artikel bietet eine Problemumgehung für das lokale Problem mit Adobe Commerce 2.4.6-p1, bei dem die Installation von [!DNL B2B] Version 1.4.0 fehlschlägt.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.6-p1 **On-Premises**
* [!DNL B2B] Version 1.4.0

>[!NOTE]
>
>[!DNL B2B] Version 1.4.0 wird erfolgreich auf **Adobe Commerce Cloud 2.4.6-p1** installiert.

## Problem

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce 2.4.6-p1.

   ```bash
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Versuchen Sie, [!DNL B2B] Version 1.4.0 zu installieren.

   ```bash
   composer require magento/extension-b2b:1.4.0
   ```

<u>Erwartete Ergebnisse</u>:

[!DNL B2B] Version 1.4.0 wird erfolgreich auf Adobe Commerce 2.4.6-p1 installiert.

<u>Tatsächliche Ergebnisse</u>:

Die Installation schlägt mit dem folgenden Fehler fehl:

```bash
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Abhilfe

Installieren Sie [!DNL B2B] Version 1.4.0 auf Adobe Commerce 2.4.6-p1 erfolgreich oder aktualisieren Sie sie, indem Sie manuelle Abhängigkeiten für das [!DNL B2B]-Sicherheitspaket mit einem [Stabilitäts-Tag](https://getcomposer.org/doc/04-schema.md#package-links) hinzufügen.

1. Aktualisieren Sie `composer.json` im Adobe Commerce-Installationsverzeichnis mit den erforderlichen Abhängigkeiten:

   ```bash
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Befehlsausgabe:**

   ```bash
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Aktualisieren Sie `composer.json` , um [!DNL B2B] Version 1.4.0 hinzuzufügen.

   ```bash
   composer require magento/extension-b2b=1.4.0
   ```

   **Befehlsausgabe:**

   ```bash
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Installation oder Upgrade abschließen.

   * [Installation  [!DNL B2B]  Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html?lang=de)
   * [On-Premise installieren](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html?lang=de)
