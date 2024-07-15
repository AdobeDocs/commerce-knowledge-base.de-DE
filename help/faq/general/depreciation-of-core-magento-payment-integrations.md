---
title: Abschreibungen der Adobe Commerce-Zahlungsintegrationen
description: Aufgrund der Zahlungsdienstrichtlinie PSD2 (siehe Einzelheiten [Zahlungsdienstrichtlinie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) in unserem Benutzerhandbuch) und der kontinuierlichen Weiterentwicklung vieler APIs besteht die Gefahr, dass einige Adobe Commerce-Kernzahlenintegrationen veraltet sind und zukünftig nicht mehr sicherheitskonform sind. Zu diesem Zweck wurden bzw. werden viele zentrale Zahlungsintegrationen eingestellt, und wir empfehlen einen Übergang zu den entsprechenden Commerce Marketplace-Erweiterungen. Lesen Sie den Rest des Artikels unten, um aktuelle veraltete Zahlungsintegrationen zu überprüfen. Jeder der **Status**-Links finden Sie in unserem Benutzerhandbuch. **Die folgenden Integrationen werden alle aus Version 2.4.0 von Adobe Commerce entfernt und sind von Version 2.3 nicht mehr unterstützt.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Abschreibungen der Adobe Commerce-Zahlungsintegrationen

Aufgrund der PSD2 der Zahlungsdienstrichtlinie (siehe Einzelheiten zur [Zahlungsdienstrichtlinie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) in unserem Benutzerhandbuch) und der kontinuierlichen Weiterentwicklung vieler APIs besteht die Gefahr, dass einige Kernintegrationen der Adobe Commerce-Zahlungsdienste veraltet sind und zukünftig nicht mehr sicherheitskonform sind. Zu diesem Zweck wurden bzw. werden viele zentrale Zahlungsintegrationen eingestellt, und wir empfehlen einen Übergang zu den entsprechenden Commerce Marketplace-Erweiterungen. Lesen Sie den Rest des Artikels unten, um aktuelle veraltete Zahlungsintegrationen zu überprüfen. Jeder der **Status**-Links finden Sie in unserem Benutzerhandbuch. **Die folgenden Integrationen werden aus Version 2.4.0 von Adobe Commerce entfernt und sind von Version 2.3 nicht mehr unterstützt.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Zahlungsmethodenintegration</strong></td>
<td style="width: 226.364px;"><strong>Status</strong></td>
<td style="width: 226.364px;"><strong>Adobe Commerce 2.x-Empfehlung</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.5</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Fragen Sie Ihren Zahlungsdienstleister, welche Lösung er empfiehlt, um die PSD2-Anforderungen zu erfüllen.</td>
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
<td style="width: 225.455px;">CyberSource</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.3</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Verwenden Sie stattdessen die <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">offizielle Erweiterung</a> von Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Veraltet seit 2.3.3</a><br>2.4.0 - wird vollständig entfernt</td>
<td style="width: 226.364px;">Fragen Sie Ihren Zahlungsdienstleister, welche Lösung er empfiehlt, um die PSD2-Anforderungen zu erfüllen.</td>
</tr>
</tbody>
</table>

**Bitte beachten Sie, dass die Integration der PayPal-Core-Zahlungsmethode nicht veraltet oder entfernt wird und für alle Versionen 2.3.x und 2.4.x weiterhin unterstützt wird.**

## Sichere Weiterleitung Ihrer Zahlungen

Befolgen Sie für alle Adobe Commerce- und Magento Open Source-Bereitstellungen, die noch nicht mehr unterstützt werden, die unten stehenden Empfehlungen, um sicherzustellen, dass die Zahlungen Ihrer Kunden sicher sind, dass die Zahlungen nicht abgelehnt werden, und um sich auf die Aktualisierung auf Adobe Commerce 2.4.0 vorzubereiten:

* Installieren und konfigurieren Sie die offizielle Zahlungsmethodenerweiterung von [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043), wie in der obigen Tabelle angegeben.
* Deaktivieren Sie nicht mehr unterstützte Zahlungsintegrationen in Admin (stellen Sie die Konfigurationsoption **Aktiviert** auf *Nein* ein), damit sie nicht mehr in Ihrer Storefront als Zahlungsoptionen angezeigt werden. Stellen Sie sicher, dass alle neuen Bestellungen stattdessen über die Erweiterungsintegration bezahlt werden.
* Da die neue Integration von Commerce Marketplace nicht in der Lage sein wird, Zahlungsvorgänge mithilfe einer veralteten Zahlungsintegration zu verarbeiten, empfehlen wir, beide Zahlungsmethoden für einen bestimmten Zeitraum parallel zu verwenden, jedoch nur für den Abschluss bereits eingegangener Transaktionen und möglicher Erstattungen. Lassen Sie dazu die veraltete Zahlungsmethode deaktiviert, aber alle Konfigurationsfelder ausgefüllt.
