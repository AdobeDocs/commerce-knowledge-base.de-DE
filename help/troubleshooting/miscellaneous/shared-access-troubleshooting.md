---
title: Fehlerbehebung bei freigegebenen Zugriffen
description: '**Problem:** Sie möchten Ihrem vertrauenswürdigen Kollegen freigegebenen Zugriff gewähren, aber Sie können die Registerkarte **Freigegebener Zugriff** auf Ihrer Commerce-Kontoseite nicht finden.'
exl-id: 9e03c031-2359-42a6-9de4-943451a16456
feature: Cache
role: Developer
source-git-commit: 6529a7d2c080a410617af8c51893c79c65c0bb81
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Fehlerbehebung bei freigegebenen Zugriffen

## Die Registerkarte &quot;[!UICONTROL Shared Access]&quot; wird auf meiner Commerce-Kontoseite (Kontoinhaber) nicht angezeigt.

**Problem:** Sie möchten Ihrem vertrauenswürdigen Kollegen freigegebenen Zugriff gewähren, aber Sie können die Registerkarte **[!UICONTROL Shared Access]** nicht auf Ihrer Commerce-Kontoseite finden.

**Mögliche Ursache:** Die für die Gewährung des gemeinsamen Zugriffs erforderlichen Berechtigungen wurden nicht mit Ihrem Commerce-Konto verknüpft.

**Lösung:**

* Wenden Sie sich an Ihr Adobe-Account-Team, wenn Sie der Kontoinhaber sind. Wenn Ihr Team-Mitglied Zugriff auf Support hat, lassen Sie es [ein Support-Ticket erstellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#merchant-not-displayed). Geben Sie den Namen und die E-Mail-Adresse an, die mit Ihrem Konto verknüpft sind.
* Wenn Sie nicht der Kontoinhaber sind, müssen Sie sich an diese wenden, um freigegebenen Zugriff und die erforderlichen Berechtigungen bereitzustellen.
* Wenn der Kontoinhaber nicht mehr im Unternehmen ist und Sie das Konto an einen anderen Benutzer übertragen möchten, lesen Sie den Abschnitt [Übertragen eines Commerce-Kontos](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-transfer).

>[!NOTE]
>
>Es ist auch möglich, dass ein Nicht-Kontoinhaber die Registerkarte [!UICONTROL Shared Access] in seinem Konto hat. Allerdings kann nur der Kontoinhaber (der primäre Kontoinhaber) mit den erforderlichen Berechtigungen einen gemeinsamen Zugriff für andere Benutzer bereitstellen. Weitere Informationen zum freigegebenen Zugriff finden Sie unter [Freigegebener Zugriff: Gewähren Sie anderen Benutzern Zugriff auf Ihr Konto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#shared-access) im Experience League Support-Benutzerhandbuch für Adobe Commerce.

## Ich habe freigegebenen Zugriff verwendet, kann aber keinen Zugriff auf eine bestimmte Ressource erhalten

**Problem:** Ich bin zum [!UICONTROL Shared Access] -Konto gewechselt, kann aber nicht auf den **[!UICONTROL Support tab]** zugreifen (z. B.).

**Mögliche Ursache:** Die Unterstützungsberechtigungen sind abgelaufen oder Sie erhalten keinen freigegebenen Zugriff auf den Support.

**Lösung:**

1. Wechseln Sie zurück zu **[!UICONTROL My Account]**.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Shared with me]** .
1. Klicken Sie auf das **[!UICONTROL Shared Access]**-Konto, bei dem Probleme auftreten, und überprüfen Sie, auf welche Ressourcen Ihnen Zugriff gewährt wurde.
1. Wenn die spezifische Ressource fehlt, wenden Sie sich an den Kontoinhaber (Primärkontoinhaber).

Wenn weiterhin Probleme auftreten, wenden Sie sich an Ihr Adobe-Account-Team. Geben Sie den Namen und die E-Mail-Adresse an, die mit Ihrem Konto verknüpft sind.

## Ich nutzte freigegebenen Zugriff und klickte auf [!UICONTROL Support]. Als ich jedoch ein neues Ticket für die Organisation öffnete, war kein Produkt im Formular verfügbar

**Problem:** Ich kann beim Öffnen eines Tickets auf [Experience League](https://experienceleague.adobe.com/home#support) nicht das entsprechende Cloud-Projekt auswählen.

**Mögliche Ursache:** Sie haben nicht die richtige Organisation mit [!DNL Commerce] Berechtigungen ausgewählt.

**Lösung:**

1. Stellen Sie sicher, dass Sie die Organisation mit dem Suffix *[!DNL Commerce]* auswählen. Dies ist die Organisation, die über die Berechtigung [!DNL Commerce] verfügt.

Wenn weiterhin Probleme auftreten, wenden Sie sich an Ihr Adobe-Account-Team. Geben Sie den Namen und die E-Mail-Adresse an, die mit Ihrem Konto verknüpft sind.

## Ich habe den freigegebenen Zugriff verwendet und auf [!UICONTROL Support] geklickt. Als ich jedoch ein neues Ticket für die Organisation geöffnet habe, die über die Berechtigung [!DNL Commerce] verfügt, wurde das Cloud-Projekt nicht im Formular aufgeführt

**Problem**: Ich kann beim Öffnen eines Tickets auf [Experience League](https://experienceleague.adobe.com/home#support) nicht das entsprechende Cloud-Projekt auswählen.

**Mögliche Ursache**: Möglicherweise wurden Sie dem Projekt nicht hinzugefügt oder das Projekt ist mit einer anderen Lizenz verbunden (einige Organisationen verfügen möglicherweise über Tochterunternehmen/verbundene Unternehmen mit sehr ähnlichen Namen).

**Lösung**:

1. Vergewissern Sie sich, dass Sie zum Projekt hinzugefügt wurden. Siehe [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/user-access).
1. Stellen Sie sicher, dass der Kontoinhaber Ihnen gemeinsamen Zugriff auf die mit dem Projekt verknüpfte Lizenz gewährt hat.

Wenn weiterhin Probleme auftreten, wenden Sie sich an Ihr Adobe-Account-Team. Geben Sie den Namen und die E-Mail-Adresse an, die mit Ihrem Konto verknüpft sind.

## Ich habe den freigegebenen Zugriff verwendet und auf [!UICONTROL Support] geklickt, aber beim Öffnen eines neuen Tickets wurde das Dropdown-Menü [!UICONTROL Organization] nicht angezeigt oder hat diese Organisation nicht aufgelistet.

**Problem**: Ich bin zum Konto [!UICONTROL Shared Access] gewechselt, aber wenn ich versuche, ein Ticket auf [Experience League](https://experienceleague.adobe.com/home#support) zu senden, ist keine Organisation verfügbar oder der Organisationsname wird nicht in der Dropdown-Liste aufgeführt.

**Mögliche Ursache**: Ihnen wurde in Ihrem Konto nur der gemeinsame Zugriff auf einen Händler gewährt.

**Lösung**:

1. Wechseln Sie zurück zu **[!UICONTROL My Account]**.
1. Wenn nur ein freigegebener Name aufgeführt wird, ist dies die Standardorganisation, unter der Ihre Tickets geöffnet werden.

Wenn weiterhin Probleme auftreten, wenden Sie sich an Ihr Adobe-Account-Team. Geben Sie den Namen und die E-Mail-Adresse an, die mit Ihrem Konto verknüpft sind.

## Ich habe den freigegebenen Zugriff verwendet, sehe aber trotzdem meine Tickets anstelle der freigegebenen

**Problem:** Ich greife über freigegebenen Zugriff auf das [Hilfe-Center](https://support.magento.com/hc/us-en/requests) zu, sehe aber immer noch nur die Tickets, die zu meinem eigenen Konto (meiner Organisation) gehören. Auf der Seite [!DNL Commerce] Konto wird angezeigt, dass ich das Konto der Organisation verwende, das mir freigegebenen Zugriff gewährt hat, die Organisations-Tickets jedoch immer noch nicht angezeigt werden.

**Mögliche Ursache:** Ihr Browser verwendet den zwischengespeicherten Inhalt aus dem Hilfezentrum.

**Lösung:** Löschen Sie Ihren Browser-Cache und greifen Sie erneut auf das Help Center zu (stellen Sie sicher, dass Sie auf Ihrer Commerce-Kontoseite auf den freigegebenen Zugriff gewechselt haben).
