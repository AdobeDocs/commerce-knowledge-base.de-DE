---
title: Aktualisieren des Cloud-Kontoprofils
description: Dieser Artikel beschreibt die Schritte zum Ändern des Profils im Cloud-Konto.
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%
---
# Aktualisieren des Cloud-Kontoprofils

Dieser Artikel enthält Schritte zum Ändern des Profils im Cloud-Konto.

## Lösung

Beim Ändern eines Profils im Cloud-Konto können die folgenden Felder geändert werden:

1. [!UICONTROL First name]
1. [!UICONTROL Last name]
1. [!UICONTROL Username]

   >[!NOTE]
   >
   >Beim Aktualisieren des Benutzernamens der Cloud-Konsole wird die Projekt-URL von `https://console.adobecommerce.com <old-username>/<project-id>` in `https://console.adobecommerce.com/<new-username>/<project-id>` geändert.
   >
   >Nach der Aktualisierung funktionieren Links, die die alte URL verwenden, nicht mehr. Die Team-Mitglieder müssen gespeicherte Lesezeichen, interne Dokumentationen und alle Automatisierungen aktualisieren, um die neue URL verwenden zu können.
   >
   >Diese Änderung gilt nur für die neue Cloud Console-URL. Die alte Projekt-URL (`https://<region>.magento.cloud/projects/<project-id>`) verwendet nicht den Benutzernamen und funktioniert weiterhin unverändert.

Gehen Sie wie folgt vor, um diese Felder zu ändern:

1. Greifen Sie unter [Adobe-Kontoanmeldung](https://accounts.magento.cloud) auf Ihr Konto zu.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Account Settings]** .
1. Aktivieren Sie das *Neues Kennwort erstellen*.
1. Nehmen Sie die erforderlichen Änderungen vor und klicken Sie auf *Speichern*.

>[!NOTE]
>
>Ihr Kennwort wird nicht geändert.

## Was kann nicht geändert werden?

1. **[!UICONTROL Password]**:
Um Ihr Kennwort zu ändern, besuchen Sie [Adobe Password Reset](https://account.adobe.com/), da dieses Profil mit Ihrem Konto/Ihrer E-Mail-Adresse dort verknüpft ist.

1. **[!UICONTROL Email Address]**:
Das Ändern dieses Felds hängt von Ihren individuellen Umständen ab.

Wenn Sie das Eigentum an Ihrem aktuellen Konto auf einen neuen Besitzer oder eine andere E-Mail-Adresse übertragen müssen, müssen Sie die mit dem Konto verknüpfte E-Mail-Adresse des primären Benutzers aktualisieren.

Siehe: [https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=de](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=de)
