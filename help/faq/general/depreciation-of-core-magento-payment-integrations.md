---
title: Abschreibung von Adobe Commerce-Kernzahlungsintegrationen
description: Aufgrund der Zahlungsdiensterichtlinie PSD2 (siehe Einzelheiten zur [Zahlungsdiensterichtlinie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) in unserem Benutzerhandbuch) und der kontinuierlichen Weiterentwicklung vieler APIs besteht die Gefahr, dass eine Reihe von Adobe Commerce-Kernzahlungsintegrationen veraltet sind und in Zukunft nicht mehr sicherheitskonform sind. Zu diesem Zweck wurden oder werden viele zentrale Zahlungsintegrationen schon bald eingestellt, und wir empfehlen einen Übergang zu den entsprechenden Commerce Marketplace-Erweiterungen. Bitte lesen Sie den Rest des folgenden Artikels, um sich über aktuelle Ausfälle bei Zahlungsintegrationen zu informieren. Jeder der **Status**-Links finden Sie in unserem Benutzerhandbuch. **Die folgenden Integrationen werden alle aus Adobe Commerce Version 2.4.0 entfernt und sind seit Version 2.3 veraltet.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Abschreibung von Adobe Commerce-Kernzahlungsintegrationen

Aufgrund der Zahlungsdiensterichtlinie PSD2 (siehe Einzelheiten zur [Zahlungsdiensterichtlinie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) in unserem Benutzerhandbuch) und der kontinuierlichen Weiterentwicklung vieler APIs besteht die Gefahr, dass eine Reihe von Adobe Commerce-Kernzahlungsintegrationen veraltet sind und in Zukunft nicht mehr sicherheitskonform sind. Zu diesem Zweck wurden oder werden viele zentrale Zahlungsintegrationen schon bald eingestellt, und wir empfehlen einen Übergang zu den entsprechenden Commerce Marketplace-Erweiterungen. Bitte lesen Sie den Rest des folgenden Artikels, um sich über aktuelle Ausfälle bei Zahlungsintegrationen zu informieren. Jeder der **Status**-Links finden Sie in unserem Benutzerhandbuch. **Die folgenden Integrationen werden alle aus Adobe Commerce Version 2.4.0 entfernt und sind seit Version 2.3.** veraltet

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Integration der Zahlungsmethode</strong></td>
<td style="width: 226.364px;"><strong>Status</strong></td>
<td style="width: 226.364px;"><strong>Empfehlung für Adobe Commerce 2.x</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.5</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Fragen Sie Ihren Zahlungsanbieter, welche Lösung er zur Erfüllung der PSD2-Anforderungen empfiehlt.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.4</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Verwenden Sie stattdessen die <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">offizielle Erweiterung</a> von Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (Direct Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.1</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Verwenden Sie stattdessen die <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">offizielle Erweiterung</a> von Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">Cyberquelle</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.3</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Verwenden Sie stattdessen die <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">offizielle Erweiterung</a> von Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">Weg</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.3</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Fragen Sie Ihren Zahlungsanbieter, welche Lösung er zur Erfüllung der PSD2-Anforderungen empfiehlt.</td>
</tr>
</tbody>
</table>

**Bitte beachten Sie, dass die Integration der PayPal-Kernzahlungsmethode nicht eingestellt oder entfernt wird und für alle Versionen 2.3.x und 2.4.x weiterhin unterstützt wird.**

## Wie Sie Ihre Zahlungen sicher halten können

Befolgen Sie bei allen Adobe Commerce- und Magento Open Source-Bereitstellungen, in denen noch veraltete Zahlungsintegrationen verwendet werden, die folgenden Empfehlungen, um sicherzustellen, dass die Zahlungen Ihrer Kunden sicher sind, dass sie nicht abgelehnt werden, und um sich auf das Upgrade auf Adobe Commerce 2.4.0 vorzubereiten:

* Installieren und konfigurieren Sie die offizielle Zahlungsmethodenerweiterung von [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043) wie in der obigen Tabelle beschrieben.
* Veraltete Zahlungsintegrationen in Admin deaktivieren (die Konfigurationsoption **Aktiviert** auf *Nein* setzen), damit sie nicht mehr als Zahlungsoptionen in Ihrer Storefront angezeigt werden. Stellen Sie sicher, dass alle neuen Bestellungen stattdessen über die Erweiterungsintegration bezahlt werden.
* Da die neue Integration von Commerce Marketplace nicht mehr in der Lage sein wird, Zahlungsvorgänge zu verarbeiten, die mit einer veralteten Zahlungsintegration durchgeführt wurden, empfehlen wir, beide Zahlungsmethoden für einen Zeitraum parallel zu verwenden, jedoch nur für den Abschluss bereits gebuchter Transaktionen und mögliche Erstattungen. Lassen Sie dazu die veraltete Zahlungsmethode deaktiviert, aber alle Konfigurationsfelder ausgefüllt.
