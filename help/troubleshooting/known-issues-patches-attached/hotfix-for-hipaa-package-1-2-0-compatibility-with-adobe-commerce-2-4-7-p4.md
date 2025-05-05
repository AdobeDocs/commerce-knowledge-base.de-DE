---
title: Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0-Kompatibilitätspaket Hotfix
description: Dieser Artikel enthält einen Hotfix, um Kompatibilität für das neue  [!DNL HIPAA]  1.2.0 mit Adobe Commerce on Cloud Infrastructure 2.4.7-p4 hinzuzufügen
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0-Kompatibilitätspaket Hotfix

Dieser Artikel enthält einen Hotfix, um Kompatibilität für das neue **[!DNL HIPAA]-Paket 1.2.0** Adobe Commerce on Cloud Infrastructure 2.4.7-p4 hinzuzufügen.

Das Problem wird in der Version 2.4.7-p5 behoben.

## Betroffene Versionen und Produkte

Adobe Commerce auf Cloud-Infrastruktur 2.4.7-p4 und früher

## Voraussetzungen

* Adobe hat Ihr Adobe Commerce-Konto für den Zugriff auf die **[!DNL HIPAA Ready]** bereitgestellt. Weitere [[!DNL HIPAA]  finden Sie in ](https://experienceleague.adobe.com/de/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) **Adobe Commerce: Erste Schritte** unter „Bereitschaft für Adobe Commerce&quot;.
* Zugriff auf [repo.magento.com](https://repo.magento.com) zur Installation der Erweiterung. Informationen zum Generieren von Schlüsseln und zum Abrufen der erforderlichen Berechtigungen finden Sie [Abrufen Ihrer Authentifizierungsschlüssel](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) in unserem **Adobe Commerce: Installationshandbuch**.

## Problem

Das [!DNL HIPAA]-Paket 1.1.0 ist nicht kompatibel mit Adobe Commerce 2.4.7x.

## Lösung

Über diesen Hotfix können Händler, die Adobe Commerce auf Cloud-Infrastruktur 2.4.7-p4 ausführen, das [!DNL HIPAA]-Paket 1.2.0 verwenden.

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0 ist nur mit Adobe Commerce 2.4.7-p5 kompatibel. Wenn Sie Kompatibilität mit [!DNL HIPAA] 1.2.0 zu Adobe Commerce 2.4.7-p4 hinzufügen möchten, installieren Sie bitte den bereitgestellten Patch.<br><u>Wenn Sie Adobe Commerce 2.4.7-p4 nicht verwenden, müssen Sie zunächst ein Upgrade auf Adobe Commerce 2.4.7-p4 durchführen, um diesen Patch verwenden zu können</u>.**

Um das Problem für Adobe Commerce in Cloud-Infrastruktur 2.4.7-p4 zu beheben, sollten Sie den Patch anwenden:

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## Anbringen des Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=de)Wissensdatenbank die Anleitung „So wenden Sie einen von Adobe bereitgestellten Composer-Patch an“.

## Nur für Adobe Commerce on Cloud-Händler - Ermitteln, ob der Patch angewendet wurde

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der Patch erfolgreich angewendet wurde.

>[!NOTE]
>
><u>Gehen Sie dazu wie folgt vor und verwenden Sie die Datei `VULN-27015-2.4.7_COMPOSER.patch` **als Beispiel**</u>:

1. [Installieren Sie das Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de).
1. Führen Sie den folgenden Befehl aus:<br>
   ![CVE-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Es sollte eine ähnliche Ausgabe angezeigt werden, **<u>wobei das hier verwendete Beispiel, VULN-27015</u>**, den Status *Angewendet* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
