---
title: productSearch查询
description: “Adobe Commerce Catalog Service的‘productSearch’ GraphQL查询的参考指南。”
source-git-commit: 49692cf4375ebb975b2cf132d21ac8debe609a90
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# productSearch查询

Adobe Commerce目录服务 `productSearch` 查询可以使用实时搜索返回有关指定为输入的SKU的详细信息。 尽管此查询与 [`productSearch` 查询](https://devdocs.magento.com//live-search/product-search.html)，实时搜索会返回 `productView` 对象。 请参阅 [`productSearch` 查询](https://devdocs.magento.com//live-search/product-search.html) 参考信息主题。

## 语法

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
```

## 必需标题

必须指定以下HTTP标头才能运行此查询。

| 标题 | 描述 |
|--- | ---|
| `Magento-Customer-Group` | 对于店面客户，此值将在 `dataservices_customer_group` cookie。 |
| `Magento-Environment-Id` | 此值可通过运行 `bin/magento config:show services_connector/services_id/environment_id` 命令。 请参阅 [商务服务](https://docs.magento.com/user-guide/configuration/services/saas.html) |
| `Magento-Store-Code` | 分配给与活动存储视图关联的存储的代码。 例如， `main_website_store`. |
| `Magento-Store-View-Code` | 分配给活动存储视图的代码。 例如， `default`. |
| `Magento-Website-Code` | 分配给与活动商店视图关联的网站的代码。 例如， `base`. |
| `X-Api-Key` | 在载入过程中生成的唯一键。 |

## 用法示例

在以下示例中，查询会返回与上一个示例相同产品的信息。 但是，它的构建是为了在目录服务中返回项目信息 `productView` 对象而不是核心 `product` 对象。 请注意，定价信息会因产品类型而异。 为简便起见，不显示方面信息。

**请求：**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
              }
            }
          }
        }
        ... on ComplexProductView {
          options {
            id
            title
            required
            values {
              id
              title
            }
          }
          priceRange {
            maximum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
          }
        }
      }
    }
  }
}
```

**响应：**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
