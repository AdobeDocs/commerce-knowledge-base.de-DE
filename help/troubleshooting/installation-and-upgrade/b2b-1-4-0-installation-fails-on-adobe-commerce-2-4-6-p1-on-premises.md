---
title: '[!DNL B2B] 1.4.0 Installation schlägt bei Adobe Commerce 2.4.6-p1 vor.'
description: Dieser Artikel bietet eine Problemumgehung für das Problem mit Adobe Commerce 2.4.6-p1 vor Ort, bei dem [!DNL B2B] Installation der Version 1.4.0 schlägt fehl.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# [!DNL B2B] 1.4.0 Installation schlägt bei Adobe Commerce 2.4.6-p1 vor Ort fehl

Dieser Artikel bietet eine Problemumgehung für das Problem mit Adobe Commerce 2.4.6-p1 vor Ort, bei dem [!DNL B2B] Installation der Version 1.4.0 schlägt fehl.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.6-p1 **vor Ort**
* [!DNL B2B] Version 1.4.0

>[!NOTE]
>
>[!DNL B2B] Version 1.4.0 erfolgreich installiert auf **Adobe Commerce Cloud 2.4.6-p1**.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce 2.4.6-p1.

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Versuchen Sie zu installieren [!DNL B2B] Version 1.4.0.

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u>Erwartete Ergebnisse</u>:

[!DNL B2B] Version 1.4.0 wird erfolgreich auf Adobe Commerce 2.4.6-p1 installiert.

<u>Tatsächliche Ergebnisse</u>:

Die Installation schlägt mit dem folgenden Fehler fehl:

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Workaround

Erfolgreiche Installation oder Aktualisierung auf [!DNL B2B] Version 1.4.0 auf Adobe Commerce 2.4.6-p1 durch Hinzufügen manueller Abhängigkeiten für die [!DNL B2B] Sicherheitspaket mit [Stabilitäts-Tag](https://getcomposer.org/doc/04-schema.md#package-links).

1. Aktualisieren Sie im Adobe Commerce-Installationsordner die `composer.json` mit den erforderlichen Abhängigkeiten:

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Befehlsausgabe:**

   ```terminal
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

1. Aktualisieren `composer.json` hinzugefügt werden [!DNL B2B] Version 1.4.0.

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **Befehlsausgabe:**

   ```terminal
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

1. Führen Sie die Installation oder Aktualisierung durch.

   * [Installieren [!DNL B2B] zur Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [Vor Ort installieren](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
