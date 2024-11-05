---
title: Konfigurieren der Adobe Commerce Intelligence-Verbindung für bestehende Cloud Starter-Projekte
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie die Adobe Commerce Intelligence-Verbindung für ein vorhandenes Cloud Starter-Projekt konfigurieren möchten.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Konfigurieren der Adobe Commerce Intelligence-Verbindung für bestehende Cloud Starter-Projekte

>[!NOTE]
>
>Adobe Commerce Intelligence wurde früher als Magento Business Intelligence (MBI) bezeichnet.

Dieser Artikel bietet eine Lösung für den Fall, dass Sie die Adobe Commerce Intelligence-Verbindung für ein vorhandenes Cloud Starter-Projekt konfigurieren möchten.

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud Starter (alle Versionen)

## Problem

Sie möchten die Commerce Intelligence-Verbindung für ein vorhandenes Cloud Starter-Projekt konfigurieren.

>[!NOTE]
>
>Adobe unterstützt keine neuen Cloud Starter-Abonnements mehr. Wenn Sie jedoch über ein bestehendes Starter-Projekt verfügen, müssen Sie die folgenden Schritte ausführen, um Ihre Verbindung zu konfigurieren.

## Lösung

Um Commerce Intelligence für Cloud Starter-Projekte zu aktivieren, erstellen Sie ein Commerce Intelligence-Konto, erstellen Sie einen SSH-Schlüssel und stellen Sie schließlich eine Verbindung zu Ihrer Adobe Commerce-Datenbank her.

Führen Sie die folgenden Schritte aus:

1. Erstellen Sie Ihr Adobe Commerce Intelligence-Konto:

   * Wechseln Sie zu [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Navigieren Sie zu **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Klicken Sie auf &quot;**[!UICONTROL Create Instance]**&quot;. Wenn diese Schaltfläche nicht angezeigt wird, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater.
   * Wählen Sie Ihr Cloud Starter-Abonnement aus. Wenn Sie nur über ein Cloud Starter-Abonnement verfügen, wird dies automatisch ausgewählt.
   * Klicken Sie auf **[!UICONTROL Continue]**.
   * Geben Sie Ihre Informationen ein, um Ihr Konto zu erstellen.

   ![MBI-Konto erstellen](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Gehen Sie in Ihren Posteingang und überprüfen Sie die E-Mail-Adresse.

   ![E-Mail-Adresse überprüfen](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Erstellen Sie ein Kennwort.

   ![Kennwort erstellen](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Nach der Erstellung Ihres Kontos haben Sie die Möglichkeit, Ihrem neuen Konto Benutzer hinzuzufügen. Technische Administratoren können nun hinzugefügt werden, um die folgenden Schritte auszuführen.

   ![Benutzer hinzufügen](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Geben Sie Informationen zu Ihrem Store ein, um Ihre Voreinstellungen festzulegen.

   ![Hinzufügen von Store-Informationen](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Es gibt einige Informationen, die Sie sammeln müssen, bevor Sie Ihre Datenbank für den dritten Schritt im Onboarding-Prozess verbinden können. Sie füllen die Seite *[!UICONTROL Connect your database]* in Schritt 9 aus.

1. Erstellen Sie einen dedizierten Commerce Intelligence-Benutzer.

   * Erstellen Sie einen neuen Benutzer auf [account.adobe.com](https://account.adobe.com/).
   * Gehen Sie zu [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) , um Ihr Adobe Commerce-Konto zu generieren.
   * Warum ein neuer Benutzer? Adobe Commerce Intelligence benötigt einen zum Projekt hinzugefügten Benutzer, um kontinuierlich neue Daten abzurufen, die in das Commerce Intelligence Data Warehouse des Kontos übertragen werden. Dieser Benutzer dient als diese Verbindung. Das Hinzufügen dieses Benutzers zum Projekt erfolgt in Schritt 4.
   * Der Grund für die Verwendung eines dedizierten Commerce Intelligence-Benutzers besteht darin, zu verhindern, dass der hinzugefügte Benutzer versehentlich deaktiviert oder gelöscht und die Commerce Intelligence-Verbindung angehalten wird.

1. Fügen Sie den neu erstellten Benutzer als *Mitarbeiter* in die primäre Umgebung des Projekts ein.

   ![Benutzer als Beitragenden hinzufügen](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Rufen Sie Ihre Commerce Intelligence SSH-Schlüssel ab.

   * Navigieren Sie zur Seite &quot;**[!UICONTROL Connect your database]**&quot;der Commerce Intelligence-Benutzeroberfläche zum Einrichten und scrollen Sie nach unten zu &quot;**[!UICONTROL Encryption settings]**&quot;.
   * Wählen Sie für das Feld **[!UICONTROL Encryption Type]** **[!UICONTROL SSH Tunnel]** aus.
   * Aus dem Dropdown-Menü können Sie den bereitgestellten Magento BI Essentials Public Key kopieren und einfügen.

   ![Verschlüsselungseinstellungen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Fügen Sie dem in Schritt 5 erstellten Commerce Intelligence-Benutzer den neuen öffentlichen Magento BI Essentials-Schlüssel hinzu.

   * Wechseln Sie zu [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Melden Sie sich mit Ihren Kontoanmeldeinformationen für den neu erstellten Commerce Intelligence-Benutzer an. Gehen Sie dann zur Registerkarte **[!UICONTROL Account Settings]** .
   * Scrollen Sie auf der Seite nach unten und erweitern Sie die Dropdown-Liste für SSH-Schlüssel. Klicken Sie dann auf **[!UICONTROL Add a public key]**.

   ![Fügen Sie einen öffentlichen Schlüssel hinzu](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Fügen Sie den Magento MBI Essentials SSH Public Key von oben hinzu.

   ![Öffentlichen SSH-Schlüssel hinzufügen](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Geben Sie die Anmeldedaten für Business Intelligence Essentials [!DNL MySQL] an.

   * Aktualisieren Sie Ihre `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Aktualisieren Sie Ihre `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Hier erhalten Sie Informationen zum Verbinden Ihrer Datenbank mit Commerce Intelligence.

   Führen Sie `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` aus, um Informationen zum Verbinden Ihrer Datenbank zu erhalten.

   Sie sollten Informationen erhalten, die der folgenden Ausgabe ähneln:

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Verbinden Sie Ihre Adobe Commerce-Datenbank.

   ![Verbinden der Adobe Commerce-Datenbank](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *input*:

   * Integrationsname: [Wählen Sie einen Namen für Ihre Integration.]
   * Host: `mbi.internal`
   * Port: 3306
   * Benutzername: mbi
   * Passwort: [Eingabedokument, das in der Ausgabe von Schritt 8 bereitgestellt wird.]
   * Datenbankname: main
   * Tabellenpräfixe: [leer lassen, wenn keine Tabellenpräfixe vorhanden sind]

1. Legen Sie Ihren [!UICONTROL Timezone Settings] fest.

   ![Zeitzoneneinstellungen](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *input*

   * Datenbank: Zeitzone: UTC
   * Gewünschte Zeitzone: [Wählen Sie die Zeitzone aus, in der Ihre Daten angezeigt werden sollen.]

1. Hier erhalten Sie Informationen zu Ihren Verschlüsselungseinstellungen.

   * Die Projekt-Benutzeroberfläche bietet eine SSH-Zugriffszeichenfolge. Diese Zeichenfolge kann zum Erfassen der Informationen verwendet werden, die für die Remote-Adresse und den Benutzernamen beim Einrichten von **[!UICONTROL Encryption settings]** erforderlich sind. Wählen Sie **[!UICONTROL SSH]** aus, um Ihren Benutzernamen und Ihre Remote-Adresse anzuzeigen. Die Textzeichenfolge vor dem *@* ist Ihr Benutzername und die Textzeichenfolge nach *@* Ihre Remote-Adresse.

   ![Zugriff auf den Site-Master](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Eingabedaten für Ihren [!UICONTROL Encryption Settings].

   ![Verschlüsselungseinstellungen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *input*

   * Verschlüsselungstyp: SSH-Tunnel
   * Remote-Adresse: ssh.us-3.magento.cloud
   * Benutzername: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Port: 22

1. Klicken Sie auf **[!UICONTROL Save Integration]**.
1. Sie haben jetzt eine erfolgreiche Verbindung zu Ihrem Commerce Intelligence Essentials-Konto hergestellt.
1. Wenn Sie Adobe Commerce Intelligence Pro-Kunde sind, wenden Sie sich an Ihren Customer Success Manager oder an einen technischen Kundenberater, um die nächsten Schritte zu koordinieren.

## Verwandtes Lesen

[Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
