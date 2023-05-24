---
title: 创建自定义事件
description: 了解如何创建自定义事件，将您的Adobe Commerce数据连接到其他AdobeDX产品。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 创建自定义事件

您可以扩展 [事件平台](events.md) 通过创建自己的店面活动来收集行业独有的数据。 创建和配置自定义事件时，它会发送到 [Adobe Commerce事件收集器](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## 处理自定义事件

仅Adobe Experience Platform支持自定义事件。 自定义数据不会转发到Adobe Commerce功能板和量度跟踪器。

对于任意 `custom` 事件，则收集器会添加 `personId` (`ecid`)至 `customContext` 并封装 `xdm` 对象，然后再转发到Edge。

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
> 使用自定义事件可能会影响默认的Adobe Analytics报表。

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

通过Adobe Commerce Events SDK发布的带Adobe Commerce的产品视图覆盖：

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
