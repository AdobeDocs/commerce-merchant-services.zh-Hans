---
title: '[!DNL Catalog Service and API Mesh]'
description: ’[!DNL API Mesh] for Adobe Commerce提供了通过公共GraphQL端点集成多个数据源的方法。
exl-id: cdda4a83-3c5f-4a69-8279-b90464e16c0e
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

此 [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使开发人员能够使用Adobe I/O Runtime将专用或第三方API和其他界面与Adobe产品集成。

![目录架构图](assets/catalog-service-architecture-mesh.png)

将API网格与目录服务结合使用的第一步是将API网格连接到实例。 请参阅中的详细说明 [创建网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

要完成安装，请安装 [Adobe Developer CLI包](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

在Adobe I/O Runtime上配置Mesh后，请运行以下命令，该命令会添加 `CommerceCatalogServiceGraph` 网格的源。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

位置 `variables.json` 是一个单独的文件，用于存储Adobe I/O Runtime的常用值。
例如，API密钥可以保存在文件中：

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

运行此命令后，目录服务应通过API Mesh运行。 您可以运行 `aio api-mesh:get` 命令查看已更新网格的配置。

## API网格示例

API网格允许用户使用外部数据源来增强您的Adobe Commerce实例。 它也可用于配置现有Commerce数据以启用新功能。

### 启用层价格

在此示例中，API Mesh用于在Adobe Commerce中启用层价格。
替换 `name `， `endpoint`、和 `x-api-key` 值。

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

```graphql
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

### 获取实体ID

此网格会附加 `entityId` 到ProductView界面。 替换 `name `， `endpoint`、和 `x-api-key` 值。

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
              "endpoint": "https://catalog-service.adobe.io/graphql",
              "operationHeaders": {
                "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
                "Magento-Website-Code": "{context.headers['magento-website-code']}",
                "Magento-Store-Code": "{context.headers['magento-store-code']}",
                "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>",
                "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
              },
              "schemaHeaders": {
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>"
              }
            }
          }
        }
      ],
      "additionalTypeDefs": "extend interface ProductView {\n  entityId: String\n}\n extend type SimpleProductView {\n  entityId: String\n}\n extend type ComplexProductView {\n  entityId: String\n}\n",
      "additionalResolvers": [
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n    items {\n  sku\n uid\n  }\n    }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          },
          {
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n items {\n  sku\n uid\n }}",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          }
      ]
    }
  }
```

`entityId` 现在可以查询：

```graphql
query {
  products(skus: ["MH07"]){
    sku
    name
    id
    entityId
  }
}
```
