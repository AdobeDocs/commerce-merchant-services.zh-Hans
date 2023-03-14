---
title: '[!DNL Catalog Service and API Mesh]'
description: ‘[!DNL API Mesh] for Adobe Commerce提供了一种通过通用的GraphQL端点集成多个数据源的方法。”
source-git-commit: 41d6bed30769d3864d93d6b3d077987a810890cc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

此 [Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使开发人员能够使用Adobe I/O Runtime将专用或第三方API和其他界面与Adobe产品集成。

![目录架构图](assets/catalog-service-architecture-mesh.png)

将API网格与目录服务结合使用的第一步是将API网格连接到您的实例。 请参阅中的详细说明 [创建网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

要完成安装，请安装 [Adobe Developer CLI包](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

在Adobe I/O Runtime上配置Mesh后，运行以下命令以添加 `CommerceCatalogServiceGraph` 网格的源。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

位置 `variables.json` 是一个单独的文件，用于存储Adobe I/O Runtime的常用值。
例如，可以将API密钥保存在文件中：

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

运行此命令后， Catalog Service应通过API网格运行。 您可以运行 `aio api-mesh:get` 命令查看更新后的网格的配置。

## 使用API网格

API网格允许用户使用外部数据源，以增强您的Adobe Commerce实例。 它也可用于配置现有Commerce数据以启用新功能。

在此示例中，API Mesh用于在Adobe Commerce中启用层价格。
更换 `name `， `endpoint`、和 `x-api-key` 值。

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

配置完毕后，在Mesh中查询分层定价：

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
