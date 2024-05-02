---
title: "MDVA-37288: Falsche Tier-Preise, die nach GraphQL-Anfrage zurückgegeben wurden"
description: Der Qualitätspatch MDVA-37288 für Adobe Commerce behebt das Problem, dass nach GraphQL-Anfrage die falschen Stufenpreise zurückgegeben werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.
exl-id: d2cf24d5-6163-4968-a89c-b7407d439e1c
feature: GraphQL, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-37288: Falsche Tier-Preise, die nach GraphQL-Anfrage zurückgegeben wurden

Der Qualitätspatch MDVA-37288 für Adobe Commerce behebt das Problem, dass nach GraphQL-Anfrage die falschen Stufenpreise zurückgegeben werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.4.2 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.4.2 kompatibel.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie jedem Element die Ebenenpreise hinzu (für dieses Beispiel wurden den Artikeln mit id=1 und id=2 die Stufenpreise hinzugefügt).
1. Führen Sie eine GraphQL-Abfrage mit einer Suche aus, die die Artikel mit Tier-Preisen und Artikeln ohne Tier-Preise enthält.

<pre><code class="language-graphql">
{
  products(pageSize: 20, currentPage: 1, search: "24-MB0") {
    items {
      id
      price_tiers {
        quantity
        final_price {
          value
        }
      }
    }
  }
}
</code></pre>

<u>Erwartete Ergebnisse</u>:

Nur Artikel mit Tier-Preisen sollten angemessene Tier-Preise zurückgeben:

```json
{
  "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": []
                },
                {
                    "id": 19,
                    "price_tiers": []
                }
            ]
        }
    }
}
```

<u>Tatsächliche Ergebnisse</u>:

* Alle Artikel, die nach einem Artikel mit Stufenpreisen eingehen, haben in der Antwort einen Stufenpreis.
* Die zurückgegebenen Tier-Preisdaten stammen aus dem letzten Element in der Schleife, bei dem es zu Ebenenpreisen kam.

Antwort-Beispiel:

```json
{
    "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 19,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                }
            ]
        }
    }
}
```


## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links in unserer Entwicklerdokumentation:

* Adobe Commerce und Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html)

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster in unserer Wissensdatenbank finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) in unserer Support-Wissensdatenbank.
