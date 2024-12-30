---
title: Häufig gestellte Fragen zur Aktivierung der [!DNL Fastly]
description: In diesen häufig gestellten Fragen wird die Aktivierung der  [!DNL Fastly]  in Adobe Commerce (die seit 2021 vollständig implementiert ist) beschrieben.
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Häufig gestellte Fragen zur Aktivierung der [!DNL Fastly]

In diesen häufig gestellten Fragen wird die Aktivierung von [!DNL Fastly] in Adobe Commerce zur Verdeckung von Ursprüngen (die seit 2021 vollständig implementiert ist) behandelt.

## Was ist [!DNL Fastly] Ursprungstarnung?

Origin Cloaking ist eine Sicherheitsfunktion, die es Adobe Commerce in der Cloud-Infrastruktur ermöglicht, [!DNL non-Fastly] Traffic zu blockieren (um DDoS-Angriffe zu verhindern, gehen Sie zur Cloud-Infrastruktur (Herkunft)).

## Was sind die Vorteile von Origin Cloaking?

Das Verdecken von Ursprüngen soll verhindern, dass der Traffic die [!DNL Fastly Web Application Firewall] (WAF) umgeht, und ihn durch den streng definierten Fluss von **[!DNL Fastly]** > **Lastenausgleich** > **Instanzen** leitet. Bei dieser Implementierung fließt der gesamte Traffic durch den [!DNL Fastly] WAF sowie den internen WAF, der in den Lastenausgleich integriert ist.

## Warum findet diese ursprüngliche Cloaking-Aktivierung statt?

Diese Funktion wurde ursprünglich entwickelt, um Adobe Commerce in der Cloud-Infrastruktur zu unterstützen.

## Muss ich für mein Projekt die Aktivierung der ursprünglichen Tarnung anfordern?

Anzahl Diese Funktion sollte bereits in allen Cloud-Projekten implementiert sein. Für alle Projekte, die seit 2021 bereitgestellt wurden, wäre dies standardmäßig aktiviert.

## Ändert das Tarnen des Ursprungs die ausgehende IP-Adresse?

Nein, das tut es nicht.

## Wirkt sich das Verdecken des Ursprungs auf die REST-API aus?

[!DNL Fastly] speichert API-Aufrufe nicht zwischen, sodass der Client mit der Änderung zufrieden sein sollte. Das Verdecken des Ursprungs blockiert nur Anfragen, die direkt an den Ursprung gerichtet sind, z. B.:

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

In diesem Beispiel kann der Client weiterhin auf die API zugreifen, wenn er die URL in ``mywebsite.com`` ändert:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Beeinträchtigt diese Änderung die Bereitstellung und die Ausfallzeiten?

Nein, diese Änderung wirkt sich **NICHT** auf Bereitstellung und Ausfallzeiten aus.

## Wenn das Projekt über mehrere Staging-Umgebungen verfügt, wird die Ursprungsverdeckung auf alle Staging-Umgebungen angewendet?

Ja, wenn das Projekt über mehrere Staging-Umgebungen verfügt, wird die Änderung auf alle Staging-Umgebungen angewendet.
