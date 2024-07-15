---
title: Beheben von UTF-8-Fehlern bei CSV-Datei-Uploads
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass Sie die Fehlermeldung "CSV-Dateien müssen UTF-8-Kodierung verwenden"erhalten. Diese Fehlermeldung bedeutet, dass die Datei, die Sie hochladen möchten, unzulässige Zeichen oder Zeichen enthält, die nicht zulässig sind. Während die UTF-8-Kodierung [die meisten Zeichen](https://www.fileformat.info/info/charset/UTF-8/list.htm) zulässt, sind einige nicht mit Magento BI kompatibel.
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Beheben von UTF-8-Fehlern bei CSV-Datei-Uploads

Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass Sie die Fehlermeldung &quot;CSV-Dateien müssen UTF-8-Kodierung verwenden&quot;erhalten. Diese Fehlermeldung bedeutet, dass die Datei, die Sie hochladen möchten, unzulässige Zeichen oder Zeichen enthält, die nicht zulässig sind. Während die UTF-8-Kodierung [die meisten Zeichen](https://www.fileformat.info/info/charset/UTF-8/list.htm) zulässt, sind einige nicht mit Magento BI kompatibel.

Um das Problem zu beheben, müssen Sie die Kodierung der Datei ändern. Das erneute Speichern der Datei mit der richtigen Kodierung löst in der Regel das Problem. Beachten Sie jedoch, dass Sie dabei einige Informationen verlieren können (z. B. die unzulässigen Zeichen werden entfernt).

Es wird empfohlen, [Sublime-Text](https://www.sublimetext.com/2) zum Speichern und Kodieren der Datei zu verwenden.

1. Öffnen Sie Ihre Datei in Microsoft Excel, Google Docs, Apple Numbers oder Ihrem gewünschten Programm.
1. Klicken Sie &#x200B; auf &#x200B; **Datei** > **Speichern unter** &#x200B; und wählen Sie das Format &#x200B; **Kommagetrennte Werte (.csv)** aus, um die Datei zu speichern.
1. Öffnen Sie die CSV-Datei in Sublime Text.
1. Navigieren Sie in &quot;Text veröffentlichen&quot;zu &#x200B; &#x200B; **Datei** > **Speichern mit Kodierung** > **UTF-8\* &#x200B;** . Dadurch wird die CSV-Datei mit UTF-8-Kodierung gespeichert.    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [Laden Sie die Daten](https://docs.magento.com/mbi/data-analyst/importing-data/connecting-data/using-file-uploader.html) (in unserem Benutzerhandbuch) in eine neue Tabelle in Magento BI hoch.
