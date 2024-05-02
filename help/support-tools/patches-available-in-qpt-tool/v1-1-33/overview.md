---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.33'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.33

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.33.

QPT v1.1.33 enthält die folgenden Patches:

1. **ACSD-50478**: Behebt den Datenbankrollback-Befehl für einen Fall, in dem der DB-Dump Trigger und einen SQL-Befehl mit Trennzeichen enthält.
1. **ACSD-50512**: Behebt den Fehler: *Der herunterladbare Link steht nicht im Zusammenhang mit dem Produkt. Überprüfen Sie den Link und versuchen Sie es erneut.*  Dies geschieht beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update.
1. **ACSD-50949**: Behebung des Problems, bei dem der Preisfilter in [!UICONTROL Advanced Search] gibt bei Verwendung entlang des SKU-Filters keine korrekten Ergebnisse zurück.
1. **ACSD-51645**: Behebt den Fehler, der beim Speichern eines neuen [!UICONTROL Cart Price Rule] , wenn die Erweiterung `Magento_OfflineShipping` deaktiviert ist.
1. **ACSD-50895**: Behebt das Problem, bei dem [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM ist nicht konfiguriert.
1. **ACSD-51102**: Behebung des Problems, bei dem eine auf eine große Anzahl von Produkten angewendete Katalogregel nicht korrekt indiziert wurde, wenn die Regel durch eine geplante Aktualisierung aktiviert wurde.
1. **ACSD-50368**: Behebt das Problem, bei dem der `group_id` wird ignoriert, wenn ein Kunde über die asynchrone REST-API oder die asynchrone Bulk-REST-API erstellt wird.
1. **ACSD-51497**: Behebung des Problems, bei dem ein Kunde eine Katalogseite nicht nach [!UICONTROL Custom Attribute] des Dropdown-Typs.
1. **ACSD-51408**: Behebung des Problems, bei dem der Bestellelementstatus fälschlicherweise auf [!UICONTROL Backordered].
1. **ACSD-51735**: Behebung des Problems, bei dem der Bestellelementstatus fälschlicherweise auf [!UICONTROL Ordered] wenn der Produktbestand *0*.
1. **ACSD-51792**: Behebung des Problems, bei dem eine Seite nicht über das Impressionsereignis verfügt, wenn [!DNL Google Tag Manager] 4 ist aktiviert.
1. **ACSD-51471**: Behebung des Problems, bei dem ein Admin-Benutzer eine geplante Aktualisierung für ein gebündeltes Produkt, das ein einfaches Produkt verwendet, das selbst über eine geplante Aktualisierung verfügt, nicht speichern kann.
1. **ACSD-51700**: Behebt den Fehler, der beim Wechseln der Store-Ansichten auf einer herunterladbaren Produktebearbeitungsseite in der Admin-Konsole auftritt.
1. **ACSD-51120**: Behebung des Problems, bei dem der Cache für GraphQL-GET-Anforderungen für CMS-Seiten, die CMS-Bausteine enthalten, die über eine Staging-Aktualisierung aktualisiert werden, nicht gelöscht wird.
1. **ACSD-51240**: Behebung des Problems, bei dem die hochgeladene Datei fehlt, wenn die Registrierung über das Registrierungsformular des Unternehmens erfolgt.
1. **ACSD-51907**: Behebung des Problems, bei dem ein eingeschränkter Administrator kein Kreditmemo mit Offline-Rückerstattung erstellen kann.
1. **ACSD-52148**: Behebt das Problem, bei dem der [!UICONTROL Google V3 reCAPTCHA Admin] Die Anmeldung schlägt gelegentlich fehl.
1. **ACSD-51431**: Behebung des Problems, bei dem ein Indexerstatus funktioniert, selbst wenn keine neuen Einträge im Änderungsprotokoll vorhanden sind.
1. **ACSD-51892**: Behebung des Leistungsproblems, bei dem Konfigurationsdateien während der Bereitstellung mehrmals geladen werden.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
