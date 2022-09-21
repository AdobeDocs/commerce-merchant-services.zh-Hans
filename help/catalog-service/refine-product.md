---
title: refineProduct查询
description: “Adobe Commerce Catalog Service的‘refineProduct’ GraphQL查询的参考指南。”
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# refineProduct查询

的 `refineProduct` 查询会缩小 `products` 针对复杂产品运行的查询。 运行 `refineProduct` 查询，您必须运行 `products` 查询并构建响应，以便返回 `options` 在 `ComplexProductView` 内联片段。 当购物者在店面上选择产品选项（如大小或颜色）时，请运行 `refineProduct` ，指定SKU和选定的选项值ID作为输入。 根据复杂产品具有的产品选项数，您可能需要运行 `refineProduct` 查询多次，直到购物者选择了特定变体为止。

您应该构建查询的响应，以使其包含 `ComplexProductView` 和 `SimpleProductView` 内联片段。 如果购物者未选择所有必需选项，则查询将根据选定的选项和可能的剩余选项返回未选定选项的ID以及产品的最低和最高价格。 如果购物者选择了所有必需选项，则查询会返回有关简单产品的详细信息，该产品包括设置的价格。

## 语法

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
```

## 必需标题

必须指定以下HTTP标头才能运行此查询。

| 标题 | 描述 |
|--- | ---|
| `Magento-Customer-Group` | 对于店面客户，此值将在 `dataservices_customer_group` cookie。 |
| `Magento-Environment-Id` | 此值显示在 **系统** > **Commerce Services Connector** > **SaaS标识符** > **数据空间ID** 或通过运行 `bin/magento config:show services_connector/services_id/environment_id` 命令。 |
| `Magento-Store-Code` | 分配给与活动存储视图关联的存储的代码。 例如， `main_website_store`. |
| `Magento-Store-View-Code` | 分配给活动存储视图的代码。 例如， `default`. |
| `Magento-Website-Code` | 分配给与活动商店视图关联的网站的代码。 例如， `base`. |
| `X-Api-Key` | 在载入过程中生成的唯一键。 |

## 用法示例

### 返回有关部分选定的复杂产品的详细信息

以下查询返回有关产品中等尺寸变体可用的颜色选项的详细信息 `MH12`. 的值 `optionIDs` 输入参数取自 `products` 查询 [返回有关复杂产品的详细信息](products.md#complex-product-example) 示例。

**请求：**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### 返回有关完全选择的复杂产品的详细信息

在以下查询中，购物者选择了大小和颜色选项。 响应包含有关相应简单产品的详细信息。

**请求：**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## 输入字段

您必须指定SKU值，并至少指定一个选项ID作为输入。

| 字段 | 数据类型 | 描述 |
|--- | --- | ---|
| `optionIds` | [字符串！]! | 分配给购物者选择的产品选项的ID列表，如特定颜色和大小。 |
| `sku` | 字符串！ | 复杂产品的SKU。 |

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
