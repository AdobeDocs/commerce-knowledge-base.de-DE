---
title: "[!DNL Fastly] Häufig gestellte Fragen zur Aktivierung der Ursprungsverschlüsselung"
description: Diese FAQs behandeln häufige Fragen zu [!DNL Fastly] Aktivierung der Herkunftsverdeckung in Adobe Commerce (die seit 2021 vollständig implementiert ist).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 348a1f6e455aff9ad7c562ea20c95f27c9ee0b86
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# [!DNL Fastly] Häufig gestellte Fragen zur Aktivierung der Ursprungsverschlüsselung

Diese FAQs behandeln häufige Fragen zu [!DNL Fastly] Aktivierung der Herkunftsverdeckung in Adobe Commerce (die seit 2021 vollständig implementiert ist).

## Was ist [!DNL Fastly] Ursprungsverstopfung?

Die Herkunftsangabe ist eine Sicherheitsfunktion, mit der Adobe Commerce in der Cloud-Infrastruktur alle [!DNL non-Fastly] Traffic (zur Vermeidung von DDoS-Angriffen), der zur Cloud-Infrastruktur (Ursprung) geleitet wird.

## Was sind die Vorteile der Ursprungsverschleierung?

Die ursprüngliche Maskierung soll verhindern, dass der Traffic die [!DNL Fastly Web Application Firewall] (WAF) und Routing durch den genau definierten Fluss von **[!DNL Fastly]** > **Lastenausgleich** > **Instanzen**. Mit dieser Implementierung wird der gesamte Traffic garantiert durch den [!DNL Fastly] WAF sowie die interne WAF, die in den Lastenausgleich integriert ist.

## Warum geschieht diese Ursprungs-Maskierung?

Diese Funktion wurde ursprünglich erstellt, um Adobe Commerce in der Cloud-Infrastruktur zu nutzen.

## Muss ich die Aktivierung der Herkunftsverdeckung für mein Projekt anfordern?

Anzahl Diese Funktion hätte bereits für alle Cloud-Projekte implementiert werden müssen und für alle Projekte, die seit 2021 bereitgestellt wurden, wäre diese standardmäßig aktiviert worden. Sie können jedoch verlangen, dass die Ursprungs-Maskierung für Ihr Projekt deaktiviert wird durch [Support anfordern](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Ändert die Ursprungsangabe die ausgehende IP-Adresse?

Nein, nicht.

## Beeinflusst die Ursprungsverdeckung die REST-API?

[!DNL Fastly] speichert API-Aufrufe nicht zwischen. Daher sollte der Client mit der Änderung in Ordnung sein. Das Ursprungs-Cloaking blockiert nur Anforderungen, die direkt zum Ursprung führen, z. B.:

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

In diesem Beispiel kann der Client weiterhin die API aufrufen, wenn er die URL in ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Wird sich diese Änderung auf die Bereitstellung und Ausfallzeiten auswirken?

Nein, diese Änderung wird **NOT** Auswirkungen auf die Bereitstellung und Ausfallzeiten.

## Wenn das Projekt über mehrere Staging-Umgebungen verfügt, wird das Ursprungs-Cloaking auf alle Staging-Umgebungen angewendet?

Ja, wenn das Projekt über mehrere Staging-Umgebungen verfügt, wird die Änderung auf alle Staging-Umgebungen angewendet.
