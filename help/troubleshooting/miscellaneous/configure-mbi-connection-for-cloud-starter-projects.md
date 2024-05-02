---
title: Konfigurieren der Adobe Commerce Intelligence-Verbindung für vorhandene Cloud Starter-Projekte
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie die Adobe Commerce Intelligence-Verbindung für ein vorhandenes Cloud Starter-Projekt konfigurieren möchten.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Konfigurieren der Adobe Commerce Intelligence-Verbindung für vorhandene Cloud Starter-Projekte

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

   * Navigieren Sie zu [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Navigieren Sie zu **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Klicken Sie auf **[!UICONTROL Create Instance]**. Wenn diese Schaltfläche nicht angezeigt wird, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater.
   * Wählen Sie Ihr Cloud Starter-Abonnement aus. Wenn Sie nur über ein Cloud Starter-Abonnement verfügen, wird dies automatisch ausgewählt.
   * Klicks **[!UICONTROL Continue]**.
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

   Es gibt einige Informationen, die Sie sammeln müssen, bevor Sie Ihre Datenbank für den dritten Schritt im Onboarding-Prozess verbinden können. Sie werden die *[!UICONTROL Connect your database]* Seite in Schritt 9.

1. Erstellen Sie einen dedizierten Commerce Intelligence-Benutzer.

   * Erstellen Sie einen neuen Benutzer auf [account.adobe.com](https://account.adobe.com/).
   * Navigieren Sie zu [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) , um Ihr Adobe Commerce-Konto zu generieren.
   * Warum ein neuer Benutzer? Adobe Commerce Intelligence benötigt einen zum Projekt hinzugefügten Benutzer, um kontinuierlich neue Daten abzurufen, die in das Commerce Intelligence-Data Warehouse des Kontos übertragen werden. Dieser Benutzer dient als diese Verbindung. Das Hinzufügen dieses Benutzers zum Projekt erfolgt in Schritt 4.
   * Der Grund für die Verwendung eines dedizierten Commerce Intelligence-Benutzers besteht darin, zu verhindern, dass der hinzugefügte Benutzer versehentlich deaktiviert oder gelöscht wird, und die Commerce Intelligence-Verbindung zu stoppen.

1. Fügen Sie den neu erstellten Benutzer zur primären Umgebung des Projekts als *Mitarbeiter*.

   ![Benutzer als Mitarbeiter hinzufügen](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Rufen Sie Ihre Commerce Intelligence SSH-Schlüssel ab.

   * Navigieren Sie zu **[!UICONTROL Connect your database]** Seite der Commerce Intelligence-Benutzeroberfläche einrichten und nach unten scrollen **[!UICONTROL Encryption settings]**.
   * Für das Feld **[!UICONTROL Encryption Type]** auswählen **[!UICONTROL SSH Tunnel]**.
   * Aus dem Dropdown-Menü können Sie den bereitgestellten Magento BI Essentials Public Key kopieren und einfügen.

   ![Verschlüsselungseinstellungen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Fügen Sie dem in Schritt 5 erstellten Commerce Intelligence-Benutzer den neuen öffentlichen Schlüssel für Magento BI Essentials hinzu.

   * Navigieren Sie zu [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Melden Sie sich mit Ihren Kontoanmeldeinformationen für den neuen Commerce Intelligence-Benutzer an, der erstellt wurde. Gehen Sie dann zu **[!UICONTROL Account Settings]** Registerkarte.
   * Scrollen Sie auf der Seite nach unten und erweitern Sie die Dropdown-Liste für SSH-Schlüssel. Klicken Sie anschließend auf **[!UICONTROL Add a public key]**.

   ![Öffentlichen Schlüssel hinzufügen](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Fügen Sie den Magento MBI Essentials SSH Public Key von oben hinzu.

   ![SSH Public Key hinzufügen](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Geben Sie die MySQL-Anmeldeinformationen von Business Intelligence Essentials an.

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

   Ausführen `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` um Informationen zum Verbinden Ihrer Datenbank zu erhalten.

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

   ![Verbinden Ihrer Adobe Commerce-Datenbank](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Eingaben*:

   * Integrationsname: [Wählen Sie einen Namen für Ihre Integration aus.]
   * Host: `mbi.internal`
   * Port: 3306
   * Benutzername: mbi
   * Kennwort: [Eingabedokument, das in der Ausgabe von Schritt 8 bereitgestellt wird.]
   * Datenbankname: main
   * Tabellenpräfixe: [leer lassen, wenn keine Tabellenpräfixe vorhanden sind]

1. Legen Sie Ihre [!UICONTROL Timezone Settings].

   ![Zeitzoneneinstellungen](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Eingaben*

   * Datenbank: Zeitzone: UTC
   * Gewünschte Zeitzone: [Wählen Sie die Zeitzone aus, in der Ihre Daten angezeigt werden sollen.]

1. Hier erhalten Sie Informationen zu Ihren Verschlüsselungseinstellungen.

   * Die Projekt-Benutzeroberfläche bietet eine SSH-Zugriffszeichenfolge. Diese Zeichenfolge kann zum Erfassen der Informationen verwendet werden, die für die Remote-Adresse und den Benutzernamen beim Einrichten Ihrer **[!UICONTROL Encryption settings]**. Auswählen **[!UICONTROL SSH]** um Ihren Benutzernamen und Ihre Remote-Adresse anzuzeigen. Die Textzeichenfolge vor der *@* ist Ihr Benutzername und die Textzeichenfolge nach *@* ist Ihre Remote-Adresse.

   ![Auf Site-Master zugreifen](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Eingabedaten für Ihre [!UICONTROL Encryption Settings].

   ![Verschlüsselungseinstellungen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Eingaben*

   * Verschlüsselungstyp: SSH-Tunnel
   * Remote-Adresse: ssh.us-3.magento.cloud
   * Benutzername: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Port: 22

1. Klicks **[!UICONTROL Save Integration]**.
1. Sie haben jetzt erfolgreich eine Verbindung zu Ihrem Commerce Intelligence Essentials-Konto hergestellt.
1. Wenn Sie Adobe Commerce Intelligence Pro-Kunde sind, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater, um die nächsten Schritte zu koordinieren.
