---
title: '[!DNL Admin] Anmeldung funktioniert nicht - zulässige Sitzungsmax-Größe überschritten'
description: Lösen Sie das Problem, wenn Sie versuchen, sich bei Ihrem [!DNL Admin] -Bedienfeld und das Formular wird aktualisiert und Sie können sich nicht anmelden.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin] Anmeldung funktioniert nicht - zulässige Sitzungsmax-Größe überschritten

Dieser Artikel enthält eine Fehlerbehebung für die Anmeldung bei der [!DNL Admin] -Bedienfeld, aber das Formular wird nur aktualisiert und Sie können sich nicht anmelden. Dies liegt daran, dass die Variable [!DNL Admin] Die Sitzungsgröße wurde überschritten.

## Betroffene Versionen

* Adobe Commerce vor Ort, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Es ist nicht möglich, sich bei der [!DNL Admin], da das Formular weiterhin neu geladen wird.

## Ursache

Die zulässige Sitzungsmax-Größe wird überschritten.

## Lösung

Überprüfen Sie die `var/log/support_report.log` -Datei für Fehler wie die folgenden:

*[2023-07-13T04:26:09 79 2060+00:00] report.WARNING: Sitzungsgröße von 260572 hat die zulässige Sitzungsmax. -Größe von 256000 überschritten. [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING: Sitzungsgröße von 260570 hat die zulässige Sitzungsmax. -Größe von 256000 überschritten. [][]*

Wenn diese Fehler angezeigt werden, lautet die Lösung:

<u>Adobe Commerce vor Ort</u>:
1. Erhöhen Sie die **[!UICONTROL Max Session Size in Admin]** -Wert aus der Backend-Konfiguration. Gehen Sie dazu zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Setzen Sie den Wert auf *500000* oder höher. Je nach der vorhandenen maximalen Größe, die im Fehler angezeigt wird, können Sie den Wert auch auf *0* , wodurch die Sitzungsgrößenbeschränkung entfernt wird.

<u>Adobe Commerce auf Cloud-Infrastruktur</u>:

(Auf diese Einstellung kann nur im [!DNL Admin] wenn der Bereitstellungs-/Betriebsmodus standardmäßig für Entwickler verwendet wird. In der Cloud-Umgebung ist jedoch nur der Produktionsbereitstellungsmodus zulässig.)

Um diesen Wert zu erhöhen, führen Sie diesen Befehl im Terminal (SSH) aus:

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Sie können *500000* Abhängig von der vorhandenen maximalen Größe, die im Fehler gemeldet wird, können Sie den Wert auch auf *0* , um die Sitzungsgrößenbegrenzung zu entfernen.

## Verwandte Informationen

* [Sitzungsgröße](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) im Administratorsystem-Handbuch.
* [Betriebsmodus](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) im Konfigurationshandbuch.
* [Sichere Verbindungen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) im Commerce on Cloud Infrastructure Guide.
