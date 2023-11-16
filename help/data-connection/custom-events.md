---
title: 创建自定义事件
description: 了解如何创建自定义事件以将您的Adobe Commerce数据连接到其他AdobeDX产品。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# 创建自定义事件

您可以扩展 [事件平台](events.md) 创建自己的店面活动以收集行业独特的数据。 创建和配置自定义事件时，它会发送到 [Adobe Commerce事件收集器](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-collector).

## 处理自定义事件

仅Adobe Experience Platform支持自定义事件。 自定义数据不会转发到Adobe Commerce功能板和量度跟踪器。

对于任何 `custom` 事件，收集器：

- 添加 `identityMap` 替换为 `ECID` 作为主要标识
- 包括 `email` 在 `identityMap` 作为辅助标识 _如果_ `personalEmail.address` 在事件中设置
- 将整个事件包装在 `xdm` 对象，然后再转发到边缘

示例：

通过Adobe Commerce Events SDK发布的自定义事件：

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

在Experience Platform边缘中：

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> 使用自定义事件可能影响默认的Adobe Analytics报表。

## 处理事件覆盖（自定义属性）

仅该Experience Platform支持标准事件的属性覆盖。 自定义数据不会转发到Commerce功能板和量度跟踪器。

对于具有的任何事件 `customContext`，收集器会覆盖相关上下文中设置的联接字段，其中的字段为 `customContext`. 覆盖的用例是当开发人员想要重用和扩展由已支持的事件中的页面其他部分设置的上下文时。

>[!NOTE]
>
>覆盖自定义事件时，应该为该事件类型关闭到Experience Platform的事件转发，以避免重复计数。

示例:

通过Adobe Commerce Events SDK发布的带覆盖的产品视图：

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

在Experience Platform边缘中：

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> 使用自定义属性覆盖事件可能会影响默认的Adobe Analytics报表。
