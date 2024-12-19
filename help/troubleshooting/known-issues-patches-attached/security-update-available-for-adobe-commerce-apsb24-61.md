---
title: Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB24-61]
promoted: true
description: Wenden Sie einen isolierten Patch an,  [!DNL CVE-2024-39397]  die Instanzen Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10 und frühere Versionen nur ausgeführt werden [!DNL Apache].
feature: Compliance, Security
role: Developer
exl-id: 340b7066-e6d9-4d91-adb0-5b8860c2a5a0
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB24-61]

Am 13. August 2024 veröffentlichte Adobe ein regelmäßig geplantes Sicherheits-Update für Adobe Commerce, Magento Open Source und das Adobe Commerce Webhooks-Plug-in.
Dieses Update behebt [[!DNL critical, important] und  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) Schwachstellen. Eine erfolgreiche Ausnutzung kann zur Ausführung von beliebigem Code, zum Lesen beliebiger Dateisysteme, zur Umgehung von Sicherheitsfunktionen und zur Erweiterung von Berechtigungen führen. Das Bulletin ist [Adobe-Sicherheitsbulletin ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

>[!NOTE]
>
>**[!DNL CVE-2024-39397], die im obigen Sicherheitsbulletin aufgeführt sind, gilt nur bei Verwendung des [!DNL Apache]-Webservers.** Um sicherzustellen, dass die Behebung dieser Sicherheitslücke so schnell wie möglich angewendet werden kann, hat Adobe auch einen isolierten Patch veröffentlicht, der [!DNL CVE-2024-39397] behebt.

**Bitte wenden Sie die neuesten Sicherheitsupdates so bald wie möglich an. Wenn Sie dies nicht tun, sind Sie anfällig für diese Sicherheitsprobleme, und Adobe hat nur begrenzte Mittel, um Abhilfe zu schaffen.**

>[!NOTE]
>
>Wenden Sie sich an den Support, wenn beim Anwenden des Sicherheits-Patches/isolierten Patches Probleme auftreten.

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud, Adobe Commerce On-Premise und Magento Open Source:

* 2.4.7-P1 und früher
* 2.4.6-P6 und früher
* 2.4.5-P8 und früher
* 2.4.4-P9 und früher

## Lösung für Adobe Commerce on Cloud, Adobe Commerce On-Premise-Software und Magento Open Source

Um die Sicherheitsanfälligkeit für die betroffenen Produkte und Versionen zu beheben, müssen Sie den [!DNL CVE-2024-39397] isolierten Patch anwenden.

## Details zu isolierten Patches

Verwenden Sie das folgende beigefügte isolierte Pflaster:

* [acsd-60551-composer-patch.zip](assets/acsd-60551-composer-patch.zip)

## Anbringen des isolierten Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)Wissensdatenbank die Anleitung „So wenden Sie einen Composer-Patch von Adobe an“.

## Nur für Adobe Commerce on Cloud-Händler - Ermitteln, ob die isolierten Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der [!DNL CVE-2024-39397] isolierte Patch erfolgreich angewendet wurde.

<u>Sie können dies tun, indem Sie die folgenden Schritte ausführen und dabei die Datei `VULN-27015-2.4.7_COMPOSER.patch` als Beispiel verwenden</u>:

1. [Installieren Sie das Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den folgenden Befehl aus:<br>
   ![CVE-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Es sollte eine ähnliche Ausgabe angezeigt werden, bei der VULN-27015 den Status *Angewendet* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Sicherheits-Updates

Für Adobe Commerce verfügbare Sicherheitsupdates:

* [Adobe-Sicherheitsbulletin ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html)
