---
title: Fehlerbehebung für 503-Fehler, der durch die Notwendigkeit verursacht wurde, die standardmäßigen Lackeinstellungen zu ändern
description: Dieser Artikel enthält Lösungen zur Fehlerbehebung bei 503-Fehlern, die dadurch verursacht werden, dass bestimmte Standardwerte des Lack-Cache für Ihren Store nicht ausreichen.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Fehlerbehebung für 503-Fehler, der durch die Notwendigkeit verursacht wurde, die standardmäßigen Lackeinstellungen zu ändern

Dieser Artikel enthält Lösungen zur Fehlerbehebung bei 503-Fehlern, die dadurch verursacht werden, dass bestimmte Standardwerte des Lack-Cache für Ihren Store nicht ausreichen.

## Problem

Wenn die Länge der von Adobe Commerce verwendeten Cache-Tags die standardmäßige Größe von 8.192 Byte von Varnish überschreitet, treten im Browser HTTP 503-Fehler (Backend-Fetch fehlgeschlagen) auf. Die Fehler können ähnlich der folgenden angezeigt werden: *Fehler 503 Backend-Abruf fehlgeschlagen. Backend-Abruf fehlgeschlagen“*

## Lösung

Um dieses Problem zu beheben, erhöhen Sie den Standardwert des `http_resp_hdr_len`-Parameters in Ihrer Varnish-Konfigurationsdatei. Der Parameter `http_resp_hdr_len` gibt die maximale Header-Länge *innerhalb* der standardmäßigen Gesamtantwortgröße von 32768 Byte an.

>[!NOTE]
>
>Wenn der `http_resp_hdr_len` 32.000 überschreitet, müssen Sie auch die standardmäßige Antwortgröße mit dem Parameter `http_resp_size` erhöhen.

1. Wenn Sie ein Benutzer mit `root` Berechtigungen sind, öffnen Sie Ihre Vanish-Konfigurationsdatei in einem Texteditor:
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * Debian: `/etc/default/varnish`
   * Ubuntu: `/etc/default/varnish`
1. Suchen Sie nach dem `http_resp_hdr_len`.
1. Wenn der Parameter nicht vorhanden ist, fügen Sie ihn nach `thread_pool_max` hinzu.
1. Legen Sie `http_resp_hdr_len` auf einen Wert fest, der der Produktzahl Ihrer größten Kategorie multipliziert mit 21 entspricht. (Jedes Produkt-Tag hat eine Länge von etwa 21 Zeichen.)    Wenn Sie beispielsweise den Wert auf 65536 Byte festlegen, sollte dies funktionieren, wenn Ihre größte Kategorie 3.000 Produkte umfasst.    Beispiel:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Legen Sie die `http_resp_size` auf einen Wert fest, der der erhöhten Länge der Antwortkopfzeile entspricht.    Beispielsweise ist die Verwendung der Summe aus erhöhter Kopfzeilenlänge und Standardantwortgröße ein guter Ausgangspunkt (z. B. 65536 + 32768 = 98304): `-p http_resp_size=98304`. Es folgt ein Snippet:

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## Timeouts für Konsistenzprüfungen {#health-check-timeouts}

Wenn Sie den Cache deaktivieren, während Varnish als Caching-Anwendung konfiguriert ist und sich Adobe Commerce im Entwicklermodus befindet, ist es möglicherweise nicht mehr möglich, sich beim Admin anzumelden.

Dies kann vorkommen, da die standardmäßige Konsistenzprüfung einen `timeout` von 2 Sekunden hat. Es kann mehr als 2 Sekunden dauern, bis die Konsistenzprüfung Informationen zu jeder Konsistenzprüfungsanfrage erfasst und zusammenführt. Wenn dies in 6 von 10 Konsistenzprüfungen auftritt, wird der Adobe Commerce-Server als fehlerhaft betrachtet. Lack liefert veraltete Inhalte, wenn der Server nicht mehr gesund ist.

Da auf den Admin über Varnish zugegriffen wird, können Sie sich nicht bei Admin anmelden, um das Caching zu aktivieren (es sei denn, Adobe Commerce wird wieder in Ordnung gebracht). Sie können jedoch den folgenden Befehl verwenden, um den Cache zu aktivieren:

```bash
$ bin/magento cache:enable
```

Weitere Informationen zur Verwendung der Befehlszeile finden Sie unter [Erste Schritte mit der Befehlszeilenkonfiguration](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/config-cli).
