---
title: '[!DNL Admin]-Anmeldung funktioniert nicht - Zulässige maximale Sitzungsgröße überschritten'
description: Beheben Sie das Problem, wenn Sie versuchen, sich bei Ihrem  [!DNL Admin] -Panel anzumelden, das Formular aktualisiert wird und Sie sich nicht anmelden können.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin]-Anmeldung funktioniert nicht - Zulässige maximale Sitzungsgröße überschritten

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie versuchen, sich bei Ihrem [!DNL Admin] Panel anzumelden, das Formular jedoch gerade aktualisiert wird und Sie sich nicht anmelden können. Dies liegt daran, dass die [!DNL Admin] Sitzungsgröße überschritten wurde.

## Betroffene Versionen

* Adobe Commerce On-Premise, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Es ist nicht möglich, sich bei der [!DNL Admin] anzumelden, da das Formular ständig neu geladen wird.

## Ursache

Die maximal zulässige Sitzungsgröße wurde überschritten.

## Lösung

Überprüfen Sie die `var/log/support_report.log` Datei auf Fehler wie die folgenden:

*[2023-07-13T04:26:09.792060+00:00] report.WARNUNG: Sitzungsgröße von 260572 überschritten Zulässige Sitzungsgröße von maximal 256000. [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNUNG: Sitzungsgröße von 260570 überschritten Zulässige Sitzungsgröße von maximal 256000.[]* []

Wenn diese Fehler angezeigt werden, lautet die Lösung wie folgt:

<u>Adobe Commerce On-Premises</u>:
1. Erhöhen Sie den **[!UICONTROL Max Session Size in Admin]** aus der Backend-Konfiguration. Gehen Sie dazu zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Legen Sie den Wert auf *500000* oder höher fest. Abhängig von der vorhandenen maximalen Größe, die im Fehler gemeldet wird - können Sie den Wert auch auf *0 setzen* wodurch die Sitzungsgrößenbeschränkung aufgehoben wird.

<u>Adobe Commerce auf Cloud-Infrastruktur</u>:

(Auf diese Einstellung kann in der [!DNL Admin] nur zugegriffen werden, wenn der Bereitstellungs-/Betriebsmodus „Standard“ oder „Entwickler“ ist. In der Cloud-Umgebung ist jedoch nur der Produktionsbereitstellungsmodus zulässig.)

Um diesen Wert zu erhöhen, führen Sie diesen Befehl im Terminal (SSH) aus:

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Sie können je nach der vorhandenen maximalen Größe, die im Fehler gemeldet wurde, auf mehr als *500000* festlegen und den Wert auf *0“*, um die Sitzungsgrößenbeschränkung aufzuheben.

## Verwandtes Lesen

* [Sitzungsgröße](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) im Handbuch für Admin-Systeme.
* [Betriebsmodus](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) im Konfigurationshandbuch.
* [Sichere Verbindungen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) im Handbuch Commerce on Cloud Infrastructure .
