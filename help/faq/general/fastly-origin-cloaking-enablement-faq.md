---
title: Häufig gestellte Fragen zur Aktivierung der Ursprungsverschlüsselung[!DNL Fastly]
description: 'In diesen häufig gestellten Fragen werden häufig gestellte Fragen zur Aktivierung der Herkunftsverdeckung in Adobe Commerce (die seit 2021 vollständig implementiert ist) behandelt. [!DNL Fastly] '
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Häufig gestellte Fragen zur Aktivierung der Ursprungsverschlüsselung[!DNL Fastly]

In diesen häufig gestellten Fragen werden häufige Fragen zur Aktivierung der Ursprungsverstopfung in Adobe Commerce (die seit 2021 vollständig implementiert ist) behandelt.[!DNL Fastly]

## Was ist [!DNL Fastly] Ursprungsverstopfung?

Die Herkunftsverdeckung ist eine Sicherheitsfunktion, mit der Adobe Commerce in der Cloud-Infrastruktur jeglichen [!DNL non-Fastly]-Traffic blockieren kann (um DDoS-Angriffe zu verhindern, der in die Cloud-Infrastruktur (Ursprung) geleitet wird.

## Was sind die Vorteile der Ursprungsverschleierung?

Das Ursprungs-Cloaking soll verhindern, dass der Traffic die [!DNL Fastly Web Application Firewall] (WAF) umgeht und durch den genau definierten Fluss von **[!DNL Fastly]** > **Lastenausgleich** > **Instanzen** weiterleitet. Mit dieser Implementierung wird garantiert der gesamte Traffic durch die [!DNL Fastly] WAF sowie die interne WAF geleitet, die in den Lastenausgleich integriert ist.

## Warum geschieht diese Ursprungs-Maskierung?

Diese Funktion wurde ursprünglich erstellt, um Adobe Commerce in der Cloud-Infrastruktur zu nutzen.

## Muss ich die Aktivierung der Herkunftsverdeckung für mein Projekt anfordern?

Anzahl Diese Funktion hätte bereits für alle Cloud-Projekte implementiert werden müssen und für alle Projekte, die seit 2021 bereitgestellt wurden, wäre diese standardmäßig aktiviert worden.

## Ändert die Ursprungsangabe die ausgehende IP-Adresse?

Nein, nicht.

## Beeinflusst die Ursprungsverdeckung die REST-API?

[!DNL Fastly] speichert API-Aufrufe nicht zwischen, daher sollte der Client mit der Änderung in Ordnung sein. Das Ursprungs-Cloaking blockiert nur Anforderungen, die direkt zum Ursprung führen, z. B.:

* Produktion

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* Staging

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* StagingX

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

In diesem Beispiel kann der Client weiterhin die API aufrufen, wenn er die URL in ``mywebsite.com`` ändert:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Wird sich diese Änderung auf die Bereitstellung und Ausfallzeiten auswirken?

Nein, diese Änderung wirkt sich **NICHT** auf die Bereitstellung und Ausfallzeiten aus.

## Wenn das Projekt über mehrere Staging-Umgebungen verfügt, wird das Ursprungs-Cloaking auf alle Staging-Umgebungen angewendet?

Ja, wenn das Projekt über mehrere Staging-Umgebungen verfügt, wird die Änderung auf alle Staging-Umgebungen angewendet.
