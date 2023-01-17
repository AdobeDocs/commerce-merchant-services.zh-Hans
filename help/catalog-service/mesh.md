---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] for Adobe Commerce提供了一种通过通用GraphQL端点集成多个数据源的方法。'
source-git-commit: 7b95be48c21e17cb6ba88d326fd061f7de2f8fb5
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

的 [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使开发人员能够使用AdobeIO将专用或第三方API及其他界面与Adobe产品集成。

将API Mesh与目录服务结合使用的第一步是将API Mesh连接到实例。 请参阅 [创建网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

要完成设置，您需要 [AdobeIO CLI包](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) 已安装。

在AdobeIO上配置Mesh后，运行以下命令，该命令将 `CommerceCatalogServiceGraph` 来源。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` 是存储AdobeIO常用值的单独文件。
例如，API密钥可以保存在文件中：

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

运行此命令后，目录服务应通过API网格运行。 您可以运行 `aio api-mesh:get` 命令查看更新网格的配置。

## 使用API网格

API网格允许用户使用外部数据源来增强您的Adobe Commerce实例。 它还可用于配置现有商务数据以启用新功能。

在此示例中，API Mesh用于在Adobe Commerce中启用层价格。
替换 `name `, `endpoint` 和 `x-api-key` 值。

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "x-api-key": "storefront-catalog-apollo",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

配置完毕后，请查询网格以获取分层定价：

```json
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```
