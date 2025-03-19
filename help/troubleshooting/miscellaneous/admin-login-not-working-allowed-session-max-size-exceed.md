---
title: '[!UICONTROL Admin]-Anmeldung funktioniert nicht - Zulässige maximale Sitzungsgröße überschritten'
description: Beheben Sie das Problem, wenn Sie versuchen, sich bei Ihrem [!UICONTROL Admin] Panel anzumelden, das Formular aktualisiert wird und Sie sich nicht anmelden können.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# [!UICONTROL Admin]-Anmeldung funktioniert nicht - Zulässige maximale Sitzungsgröße überschritten

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie versuchen, sich bei Ihrem [!UICONTROL Admin] Panel anzumelden, das Formular jedoch gerade aktualisiert wird und Sie sich nicht anmelden können oder einige Aktionen im [!UICONTROL Admin] Panel ausführen und automatisch abgemeldet werden.
Dies liegt daran, dass die [!UICONTROL Admin] [!UICONTROL Session Size] überschritten wurde.

## Betroffene Versionen

* Adobe Commerce On-Premise, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Sie an der [!UICONTROL Admin] eines der folgenden Symptome bemerken:

1. Es ist nicht möglich, sich bei der [!UICONTROL Admin] anzumelden, da das Formular ständig neu geladen wird.
1. Sie werden beim Versuch, eine Aktion durchzuführen, automatisch abgemeldet.

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

(Auf diese Einstellung kann in der [!UICONTROL Admin] nur zugegriffen werden, wenn der Bereitstellungs-/Betriebsmodus &quot;*&quot;* &quot;*&quot;*. In der Cloud-Umgebung ist jedoch nur der Produktionsbereitstellungsmodus zulässig.)

Um diesen Wert zu erhöhen, führen Sie diesen Befehl im Terminal (SSH) aus:

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Sie können je nach der vorhandenen maximalen Größe, die im Fehler gemeldet wurde, auf mehr als *500000* festlegen und den Wert auf *0“*, um die Sitzungsgrößenbeschränkung aufzuheben.

## Verwandtes Lesen

* [Sitzungsgröße](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) im Handbuch für Admin-Systeme
* [Betriebsmodus](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) im Konfigurationshandbuch
* [Sichere Verbindungen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) im Handbuch zu Commerce in Cloud-Infrastrukturen
