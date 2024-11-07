---
title: Probleme bei der Kompatibilitätsprüfung für Komponenten
description: Dieser Artikel bietet Lösungen für Konflikte mit Komponentenabhängigkeiten.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Probleme bei der Kompatibilitätsprüfung für Komponenten

Dieser Artikel bietet Lösungen für Konflikte mit Komponentenabhängigkeiten.

## Beheben von Komponentenabhängigkeitskonflikten {#resolve-component-dependency-conflicts}

Wir empfehlen Ihnen, die folgenden Lösungen in der angegebenen Reihenfolge auszuprobieren:

1. [Konfliktabhängigkeiten](#trouble-depend-conflict)
1. [Probleme mit Dateisystemberechtigungen](#trouble-depend-permission)
1. [Der Status der Komponentenabhängigkeitsprüfung ändert sich nie](#trouble-depend-state)

### Konfliktabhängigkeiten {#trouble-depend-conflict}

Die Meldung &quot;*Wir haben in Konflikt stehende Komponentenabhängigkeiten gefunden*&quot;wird angezeigt, wenn der Composer nicht bestimmen kann, welche Komponenten installiert oder aktualisiert werden sollen. Um Probleme mit der Komponentenabhängigkeit zu lösen, sollten Sie eine technische Person sein, die genau versteht, wie Composer funktioniert.

Im Folgenden finden Sie eine Beispielfehlermeldung:

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>Die angezeigte Nachricht unterscheidet sich wahrscheinlich.

Weitere Informationen zu einer Lösung finden Sie unter ](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) in unserer Support-Wissensdatenbank unter [Konflikte zwischen Komponentenabhängigkeiten .

## Probleme mit Dateisystemberechtigungen {#trouble-depend-permission}

Wenn der Eigentümer des Adobe Commerce-Dateisystems nicht über die Berechtigungen zum Schreiben in Ordner im Adobe Commerce-Dateisystem verfügt, wird eine Meldung ähnlich der folgenden angezeigt:

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Stellen Sie sicher, dass Sie Dateisystemberechtigungen festlegen, wie im Artikel [Überblick über Eigentümer und Berechtigungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) in unserer Entwicklerdokumentation beschrieben.

## Der Status der Komponentenabhängigkeitsprüfung ändert sich nie {#trouble-depend-state}

In einigen Fällen ändert sich der Status der Prüfung der Komponentenabhängigkeit nicht, selbst wenn Sie versuchen, Probleme zu beheben. In diesem Fall können Sie Dateien mit den Namen `<magento_root>/var/.update_cronjob_status` und `<magento_root>/var/.setup_cronjob_status` löschen oder umbenennen und den Komponenten-Manager erneut ausführen.

Das Umbenennen oder Entfernen dieser Dateien zwingt den Komponenten-Manager dazu, die Prüfungen erneut auszuführen.
