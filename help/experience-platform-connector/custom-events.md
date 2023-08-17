---
title: 创建自定义事件
description: 了解如何创建自定义事件以将您的Adobe Commerce数据连接到其他AdobeDX产品。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 创建自定义事件

您可以扩展 [事件平台](events.md) 创建自己的店面活动以收集行业独特的数据。 创建和配置自定义事件时，它会发送到 [Adobe Commerce事件收集器](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## 处理自定义事件

仅Adobe Experience Platform支持自定义事件。 自定义数据不会转发到Adobe Commerce功能板和量度跟踪器。

对于任何 `custom` 事件，收集器会添加 `personId` (`ecid`)到 `customContext` 并包装一个 `xdm` 对象在转发到Edge之前。

示例：

通过Adobe Commerce Events SDK发布的自定义事件：

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

在Experience Platform边缘中：

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> 使用自定义事件可能影响默认的Adobe Analytics报表。

## 处理事件覆盖（自定义属性）

仅该Experience Platform支持标准事件的属性覆盖。 自定义数据不会转发到Commerce功能板和量度跟踪器。

对于包含集的任何事件 `customContext`，收集器将覆盖 `personId` 和Adobe Analytics计数器，并转发在中设置的所有其他属性 `customContext`.

示例：

通过Adobe Commerce Events SDK发布的带覆盖的产品视图：

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

在Experience Platform边缘中：

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

通过Adobe Commerce Events SDK发布的带Adobe Commerce覆盖的产品视图：

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

在Experience Platform边缘中：

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> 使用自定义属性覆盖事件可能会影响默认的Adobe Analytics报表。
