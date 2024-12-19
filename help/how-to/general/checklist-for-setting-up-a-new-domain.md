---
title: Checkliste zum Einrichten einer neuen  [!DNL domain]
description: Dies ist eine Checkliste zum Einrichten einer neuen  [!DNL domain]  in Adobe Commerce in der Cloud-Infrastruktur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Checkliste zum Einrichten einer neuen [!DNL domain]

Dies ist eine Checkliste zum Einrichten einer neuen [!DNL domain] in Adobe Commerce auf Cloud-Infrastrukturen. Dies gilt unabhängig davon, ob Sie einfach eine neue Domain hinzufügen oder die aktuelle Domain durch eine neue ersetzen möchten.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Einrichten einer neuen Domain

### Schritt 1: Ist dies für die [!DNL Integration, Staging] oder [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] werden nicht unterstützt. Sie müssen stattdessen diese Methode verwenden: [Mehrere Websites oder Geschäfte einrichten: Lokale Installation ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in unserem Benutzerhandbuch.
* **[!DNL Staging]**: Gehen Sie zu **Schritt 2**.
* **[!DNL Production]**: Gehen Sie zu **Schritt 3**.

### Schritt 2 - [!DNL Staging environment]: Sind Sie auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Senden einer Anfrage**, um die Domain zu [!DNL Fastly, Nginx] hinzuzufügen, und konfigurieren Sie die [!DNL SSL certificate] (sowie ggf. die [!DNL Sendgrid domain]). Nachdem dies konfiguriert wurde, [ Sie die  [!DNL DNS]  mit [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Sie können sich die neue [!DNL domain] selbst [!DNL Fastly], indem Sie die Konfiguration im [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** wie in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in unserem Benutzerhandbuch aktualisieren.
>
>Wenn Sie die Domain nicht hinzufügen können, kann dies einen der folgenden Gründe haben:
>
>1. Sie migrieren die Domain in die Cloud-Umgebung, die in Ihrem eigenen [!DNL Fastly]-Service konfiguriert wurde. Senden Sie in diesem Fall eine Anfrage und fordern Sie die Delegierung der Domain an.
>1. Sie migrieren die Domain von Starter zu Pro. Reichen Sie in diesem Fall ein Ersuchen um weitere Unterstützung ein.

* **[!DNL Starter]**: [!DNL Custom domains] werden in der Staging-Umgebung nicht unterstützt.

### Schritt 3 - [!DNL Production environment]: Sind Sie auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Senden einer Anfrage**, um die Domain zu [!DNL Fastly, Nginx] hinzuzufügen, und Konfigurieren der [!DNL SSL certificate] (bei Bedarf als [!DNL Sendgrid domain]). Fahren Sie nach der Konfiguration mit **Schritt 4** fort.

>[!NOTE]
>
>Sie können sich die neue [!DNL domain] selbst [!DNL Fastly], indem Sie die Konfiguration in der [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** **[!UICONTROL Domains]** > [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in unserem Benutzerhandbuch aktualisieren.
>
>
>Wenn Sie die Domain nicht hinzufügen können, kann dies einen der folgenden Gründe haben:
>
>1. Sie migrieren die Domain von lokal in die Cloud-Umgebung, die in Ihrem eigenen [!DNL Fastly]-Service konfiguriert wurde. Senden Sie in diesem Fall eine Anfrage und fordern Sie die Delegierung der Domain an.
>1. Sie migrieren die Domain von Starter zu Pro. Reichen Sie in diesem Fall ein Ersuchen um weitere Unterstützung ein.

* **[!DNL Starter]**: Fügen Sie auf der Registerkarte **[!DNL Domains]** die [!DNL domain] zu Ihrem Projekt hinzu und **Sie dann eine Anfrage**, um die **[!DNL ACME Challenge Key]** für die [!DNL SSL certificate] anzugeben.

### Schritt 4: Ist der [!DNL domain] aktiv?

* **JA**: [Aktualisieren der  [!DNL DNS] -Konfiguration mit [!UICONTROL production] Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NEIN**: [Aktualisieren Sie die  [!DNL DNS] -Konfiguration mit [!UICONTROL development] Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Verwandtes Lesen

* [Mehrere Websites oder Geschäfte einrichten: Neu hinzufügen [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in unserem Benutzerhandbuch.
