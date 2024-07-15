---
title: Fehlerbehebung für den Fehler 503, der durch die Notwendigkeit verursacht wurde, die Standardeinstellungen für "Varnish"zu ändern
description: Dieser Artikel bietet Lösungen zur Fehlerbehebung von 503-Fehlern, die dadurch verursacht werden, dass bestimmte Varnish-Cache-Standardwerte für Ihren Store nicht ausreichen.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 9c5e993b69a98865a1142110625252da848eae04
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Fehlerbehebung für den Fehler 503, der durch die Notwendigkeit verursacht wurde, die Standardeinstellungen für &quot;Varnish&quot;zu ändern

Dieser Artikel bietet Lösungen zur Fehlerbehebung von 503-Fehlern, die dadurch verursacht werden, dass bestimmte Varnish-Cache-Standardwerte für Ihren Store nicht ausreichen.

## Problem

Wenn die Länge der von Adobe Commerce verwendeten Cache-Tags den Standardwert von Varnish von 8192 Byte überschreitet, werden im Browser HTTP 503-Fehler (Backend Fetch Failed) angezeigt. Die Fehler werden möglicherweise in etwa wie folgt angezeigt: *&quot;Fehler 503 Backend-Abruf fehlgeschlagen. Backend-Abruf fehlgeschlagen&quot;*

## Lösung

Um dieses Problem zu beheben, erhöhen Sie den Standardwert des Parameters `http_resp_hdr_len` in Ihrer Varnish-Konfigurationsdatei. Der Parameter `http_resp_hdr_len` gibt die maximale Header-Länge *innerhalb* der standardmäßigen Gesamtantwortgröße von 32768 Byte an.

>[!NOTE]
>
>Wenn der `http_resp_hdr_len` -Wert 32 K überschreitet, müssen Sie auch die standardmäßige Antwortgröße mit dem Parameter `http_resp_size` erhöhen.

1. Als Benutzer mit `root` -Berechtigungen öffnen Sie die Konfigurationsdatei &quot;Vanish&quot;in einem Texteditor:
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * Debian: `/etc/default/varnish`
   * Ubuntu: `/etc/default/varnish`
1. Suchen Sie nach dem Parameter `http_resp_hdr_len` .
1. Wenn der Parameter nicht vorhanden ist, fügen Sie ihn nach `thread_pool_max` hinzu.
1. Setzen Sie `http_resp_hdr_len` auf einen Wert, der der Anzahl der Produkte Ihrer größten Kategorie entspricht, multipliziert mit 21. (Jedes Produkt-Tag hat eine Länge von etwa 21 Zeichen.)    Die Festlegung des Werts auf 65536 Byte sollte beispielsweise funktionieren, wenn Ihre größte Kategorie 3.000 Produkte aufweist.    Beispiel:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Setzen Sie &quot;`http_resp_size`&quot;auf einen Wert, der der erhöhten Antwortheader-Länge entspricht.    Beispielsweise ist die Verwendung der Summe der erhöhten Kopfzeilenlänge und der standardmäßigen Antwortgröße ein guter Ausgangspunkt (z. B. 65536 + 32768 = 98304): `-p http_resp_size=98304`. Ein Snippet folgt:

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

## Zeitüberschreitungen bei Konsistenzprüfungen {#health-check-timeouts}

Wenn Sie den Cache deaktivieren, während &quot;Varnish&quot;als Cacheanwendung konfiguriert ist und sich Adobe Commerce im Entwicklermodus befindet, ist es möglicherweise nicht möglich, sich beim Administrator anzumelden.

Diese Situation kann auftreten, da die standardmäßige Konsistenzprüfung den Wert `timeout` von 2 Sekunden hat. Es kann mehr als 2 Sekunden dauern, bis die Konsistenzprüfung Informationen zu jeder Konsistenzprüfungsanforderung erfasst und zusammenführt. Tritt dies bei 6 von 10 Konsistenzprüfungen auf, wird der Adobe Commerce-Server als ungesund betrachtet. Varnish stellt veraltete Inhalte bereit, wenn der Server ungesund ist.

Da der Zugriff auf Admin über einen anderen Vorgang erfolgt, können Sie sich nicht bei Admin anmelden, um die Zwischenspeicherung zu aktivieren (es sei denn, Adobe Commerce wird wieder gesund). Sie können jedoch den folgenden Befehl verwenden, um den Cache zu aktivieren:

```bash
$ bin/magento cache:enable
```

Weitere Informationen zur Verwendung der Befehlszeile finden Sie unter [Erste Schritte mit der Befehlszeilenkonfiguration](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands.html).
