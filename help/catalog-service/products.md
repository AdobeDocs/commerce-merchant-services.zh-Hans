---
title: 产品查询
description: “Adobe Commerce Catalog Service的‘products’ GraphQL查询的参考指南。”
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 产品查询

Adobe Commerce目录服务 `products` 查询会返回有关指定为输入的SKU的详细信息。 尽管此查询与 [`products` 查询](https://devdocs.magento.com//guides/v2.4/graphql/queries/products.html) 与核心Adobe Commerce和Magento Open Source一起提供，但存在一些差异。

目录服务查询需要一个或多个SKU值作为输入。 查询主要用于检索信息以呈现以下类型的内容：

* 产品详细信息页面 — 您可以提供有关指定SKU标识的产品的完整详细信息。

* 产品比较页面 — 您可以检索有关多个产品的选定信息，如名称、价格和图像。

的 `ProductView` 输出对象与核心对象有显着差异 `products` 查询 `Products` 输出对象。 主要区别包括：

* 产品要么简单，要么复杂。 简单、虚拟、可下载和礼品卡产品映射到 `SimpleProductView`. 所有其他产品类型都映射到 `ComplexProductView`. 简单的产品确定了价格。 复杂产品的价格范围。 由于复杂产品由多种简单产品组成，因此它们可以获得简单的产品价格。

* 商家定义的属性在顶级容器中公开，并指示其店面角色。 角色包括在PDP上显示、在PLP上显示和在搜索结果上显示。

* 图像也可作为顶级容器访问，并可以按其角色进行过滤。 图像可以具有基本、小或缩略图角色。

## 语法

```graphql
products (skus [String]) [ProductView]
```

## 必需标题

必须指定以下HTTP标头才能运行此查询。

| 标题 | 描述 |
| --- | --- |
| `Magento-Customer-Group` | 对于店面客户，此值将在 `dataservices_customer_group` cookie。 |
| `Magento-Environment-Id` | 此值显示在 **系统** > **Commerce Services Connector** > **SaaS标识符** > **数据空间ID** 或通过运行 `bin/magento config:show services_connector/services_id/environment_id` 命令。 |
| `Magento-Store-Code` | 分配给与活动存储视图关联的存储的代码。 例如， `main_website_store`. |
| `Magento-Store-View-Code` | 分配给活动存储视图的代码。 例如， `default`. |
| `Magento-Website-Code` | 分配给与活动商店视图关联的网站的代码。 例如， `base`. |
| `X-Api-Key` | 在载入过程中生成的唯一键。 |

## 用法示例

### 返回有关简单产品的详细信息

以下查询返回有关简单产品的详细信息。

**请求：**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
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
```

**响应：**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### 返回有关复杂产品的详细信息 {#complex-product-example}

以下查询返回有关可配置产品的详细信息。

**请求：**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
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
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## 输出字段

的 `ProductView` 返回对象是一个可包含以下字段的界面。 它由 [`SimpleProductView`](#SimpleProductView-type) 和 [`ComplexProductView`](#ComplexProductView-type) 类型。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 为店面指定的商家定义属性列表。 |
| `description` | 字符串 | 产品的详细描述。 |
| `id` | ID! | 产品ID，作为复合键值生成，每个区域设置都是唯一的。 |
| `images(roles: [String])` | [ProductViewImage] | 为产品定义的图像列表。 |
| `metaDescription` | 字符串 | 搜索结果列表产品的简要概述。 |
| `metaKeyword` | 字符串 | 仅对搜索引擎可见的以逗号分隔的关键词列表。 |
| `metaTitle` | 字符串 | 在浏览器的标题栏和选项卡以及搜索结果列表中显示的字符串。 |
| `name` | 字符串 | 产品名称。 |
| `shortDescription` | 字符串 | 产品的摘要。 |
| `sku` | 字符串 | 产品SKU。 |
| `url` | 字符串 | 产品的规范URL。 |

### ComplexProductView类型 {#ComplexProductView-type}

的 `ComplexProductView` 类型表示捆绑、可配置和组产品。 复杂产品价格将作为价格范围返回，因为价格值可能因选定选项而异。 类型实施 `ProductView`.

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 为店面指定的商家定义属性列表。 |
| `description` | 字符串 | 产品的详细描述。 |
| `id` | ID! | 产品ID，作为复合键值生成，每个区域设置都是唯一的。 |
| `images(roles: [String])` | [ProductViewImage] | 为产品定义的图像列表。 |
| `metaDescription` | 字符串 | 搜索结果列表产品的简要概述。 |
| `metaKeyword` | 字符串 | 仅对搜索引擎可见的以逗号分隔的关键词列表。 |
| `metaTitle` | 字符串 | 在浏览器的标题栏和选项卡以及搜索结果列表中显示的字符串。 |
| `name` | 字符串 | 产品名称。 |
| `options` | [ProductViewOption] | 可选选项列表。 |
| `priceRange` | ProductViewPriceRange | 复杂产品的可能价格范围。 |
| `shortDescription` | 字符串 | 产品的摘要。 |

### 价格类型

的 `Price type` 定义简单产品的价格或复杂产品价格范围的一部分。 它可以包括价格调整列表。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `amount` | ProductViewMoney | 包含产品的货币值和货币代码。 |

### 价格调整类型

的 `PriceAdjustment` 类型指定价格调整的金额和类型。 示例代码值为 `weee`.

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `amount` | 浮动 | 价格调整的金额。 |
| `code` | 字符串 | 确定价格调整的类型。 |

### ProductViewAttribute类型

的 `ProductViewAttribute` type是显示在店面中的客户定义属性的容器。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `label` | 字符串 | 属性的标签。 |
| `name` | 字符串！ | 属性代码的名称。 |
| `roles` | [字符串] | 为店面上的属性指定的角色，如“在PLP上显示”、“在PDP中显示”或“在搜索中显示”。 |
| `value` | JSON | 属性值，任意类型。 |

### ProductViewImage类型

的 `ProductViewImage` 类型包含有关产品图像的详细信息。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `label` | 字符串 | 产品图像的显示标签。 |
| `roles` | [字符串] | 描述图像使用方式的列表。 可以 `image`, `small_image`或 `thumbnail`. |
| `url` | 字符串！ | 产品图像的URL。 |

### ProductViewMoney类型

的 `ProductViewMoney` 类型定义货币值，包括数值和货币代码。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `currency` | ProductViewCurrency | 三个字母的货币代码，如USD或EUR。 |
| `value` | 浮动 | 表示货币值的数字。 |

### ProductViewOption类型

产品选项提供了一种通过选择特定选项值来配置产品的方法。 选择一个或多个选项将指向特定的简单产品。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `id` | ID | 选项的ID。 |
| `multi` | 布尔值 | 指示选项是否允许多个选项。 |
| `required` | 布尔值 | 指示是否必须选择选项。 |
| `title` | 字符串 | 选项的显示名称。 |
| `values` | [ProductViewOptionValue!] | 可用选项值的列表。 |

### ProductViewOptionValue界面

的 `ProductViewOptionValue` 界面定义可用于 `ProductViewOptionValueProduct` 和 `ProductViewOptionValueConfiguration` 类型。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `id` | ID | 选项值的ID。 |
| `title` | 字符串 | 选项值的显示名称。 |

### ProductViewOptionValueConfiguration类型

的 `ProductViewOptionValueConfiguration` 类型是 `ProductViewOptionValue` 的值。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `id` | ID | 选项值的ID。 |
| `title` | 字符串 | 选项值的显示名称。 |

### ProductViewOptionValueProductType

的 `ProductViewOptionValueProduct` 类型是 `ProductViewOptionValue` 添加了有关简单产品的详细信息。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `id` | ID | 选项值的ID。 |
| `title` | 字符串 | 选项值的显示名称。 |
| `product` | SimpleProductView | 有关简单产品的详细信息。 |

### ProductViewPrice类型

的 `ProductViewPrice` type提供基本产品价格视图，这是简单产品固有的。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `final` | 价格 | 折扣后的价值，不包括个性化促销。 |
| `regular` | 价格 | 商户指定的基本产品价格。 |
| `roles` | [字符串] | 确定价格是可见还是隐藏。 |

### ProductViewPriceRange类型

的 `ProductViewPriceRange` 类型列出复杂产品的最低和最高价格。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `maximum` | ProductViewPrice | 最高价格。 |
| `minimum` | ProductViewPrice | 最低价格。 |

### SimpleProductView类型 {#SimpleProductView-type}

的 `SimpleProductView` type表示除捆绑、可配置和组之外的所有产品类型。 简单产品价格不包含价格范围。 `SimpleProductView` 实施 `ProductView`.

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 为店面指定的商家定义属性列表。 |
| `description` | 字符串 | 产品的详细描述。 |
| `id` | ID! | 产品ID，作为复合键值生成，每个区域设置都是唯一的。 |
| `images(roles: [String])` | [ProductViewImage] | 为产品定义的图像列表。 |
| `metaDescription` | 字符串 | 搜索结果列表产品的简要概述。 |
| `metaKeyword` | 字符串 | 仅对搜索引擎可见的以逗号分隔的关键词列表。 |
| `metaTitle` | 字符串 | 在浏览器的标题栏和选项卡以及搜索结果列表中显示的字符串。 |
| `name` | 字符串 | 产品名称。 |
| `price` | ProductViewPrice | 基本产品价格视图。 |
| `shortDescription` | 字符串 | 产品的摘要。 |
| `sku` | 字符串 | 产品SKU。 |
| `url` | 字符串 | 产品的规范URL。 |
