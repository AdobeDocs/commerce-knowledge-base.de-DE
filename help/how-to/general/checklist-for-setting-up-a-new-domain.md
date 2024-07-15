---
title: Checkliste zum Einrichten eines neuen  [!DNL domain]
description: Dies ist eine Checkliste, wie Sie in Adobe Commerce eine neue  [!DNL domain] in der Cloud-Infrastruktur einrichten.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Checkliste zum Einrichten einer neuen [!DNL domain]

Dies ist eine Checkliste, wie Sie in Adobe Commerce eine neue [!DNL domain] für die Cloud-Infrastruktur einrichten. Sie gilt unabhängig davon, ob Sie einfach versuchen, eine neue Domäne hinzuzufügen oder die aktuelle Domäne durch eine neue zu ersetzen.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Einrichten einer neuen Domäne

### Schritt 1: Ist dies für die [!DNL Integration, Staging] oder die [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] werden nicht unterstützt. Verwenden Sie stattdessen diese Methode: [Richten Sie mehrere Websites oder Stores ein: Konfigurieren Sie die lokale Installation](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in unserem Benutzerhandbuch.
* **[!DNL Staging]**: Gehen Sie zu **Schritt 2**.
* **[!DNL Production]**: Gehen Sie zu **Schritt 3**.

### Schritt 2 - [!DNL Staging environment]: Bist du auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Senden Sie eine Anfrage**, um die Domäne zu [!DNL Fastly, Nginx] hinzuzufügen und die [!DNL SSL certificate] zu konfigurieren (sowie ggf. die [!DNL Sendgrid domain]). Sobald dies konfiguriert wurde, aktualisiert [die [!DNL DNS] Konfiguration mit [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Sie können die neue [!DNL domain] zu [!DNL Fastly] selbst hinzufügen, indem Sie die Konfiguration in der [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** wie in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in unserem Benutzerhandbuch aktualisieren.
>
>Wenn Sie die Domäne nicht hinzufügen können, kann dies auf einen der folgenden Gründe zurückzuführen sein:
>
>1. Sie migrieren die Domäne in die Cloud-Umgebung, die in Ihrem eigenen [!DNL Fastly]-Dienst konfiguriert wurde. Senden Sie in diesem Fall eine Anfrage und beantragen Sie die Zuweisung der Domäne.
>1. Sie migrieren die Domäne von Starter zu Pro. Senden Sie in diesem Fall einen Antrag auf weitere Unterstützung.

* **[!DNL Starter]**: [!DNL Custom domains] werden in der Staging-Umgebung nicht unterstützt.

### Schritt 3 - [!DNL Production environment]: Bist du auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Senden Sie eine Anfrage**, um die Domäne zu [!DNL Fastly, Nginx] hinzuzufügen und die [!DNL SSL certificate] zu konfigurieren (bei Bedarf als [!DNL Sendgrid domain]). Sobald dies konfiguriert wurde, fahren Sie mit **Schritt 4** fort.

>[!NOTE]
>
>Sie können die neue [!DNL domain] zu [!DNL Fastly] selbst hinzufügen, indem Sie die Konfiguration in der [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in unserem Benutzerhandbuch aktualisieren.
>
>
>Wenn Sie die Domäne nicht hinzufügen können, kann dies auf einen der folgenden Gründe zurückzuführen sein:
>
>1. Sie migrieren die Domäne von lokal in die Cloud-Umgebung, die in Ihrem eigenen [!DNL Fastly]-Dienst konfiguriert wurde. Senden Sie in diesem Fall eine Anfrage und beantragen Sie die Zuweisung der Domäne.
>1. Sie migrieren die Domäne von Starter zu Pro. Senden Sie in diesem Fall einen Antrag auf weitere Unterstützung.

* **[!DNL Starter]**: Fügen Sie Ihrem Projekt auf der Registerkarte **[!DNL Domains]** den Wert [!DNL domain] hinzu und senden Sie dann **eine Anfrage**, um den Wert **[!DNL ACME Challenge Key]** für den Wert [!DNL SSL certificate] anzugeben.

### 4. Schritt - Ist der [!DNL domain] aktiv?

* **YES**: [Aktualisieren Sie die [!DNL DNS] Konfiguration mit [!UICONTROL production] settings](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO**: [Aktualisieren Sie die [!DNL DNS] Konfiguration mit [!UICONTROL development] settings](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Verwandtes Lesen

* [Richten Sie mehrere Websites oder Stores ein: Fügen Sie in unserem Benutzerhandbuch Neu [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) hinzu.
