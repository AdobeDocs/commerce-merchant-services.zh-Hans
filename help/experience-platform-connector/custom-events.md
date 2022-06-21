---
title: 创建自定义事件
description: 了解如何创建自定义事件，将您的Adobe Commerce数据与其他AdobeDX产品连接起来。
source-git-commit: 1dd8f94e632bb98666ad252badf8420a014260fb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 创建自定义事件

您可以扩展 [活动平台](events.md) 创建您自己的店面事件，以收集行业特有的数据。 创建和配置自定义事件时，该事件将发送到 [MagentoStorefront事件收集器](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

## 处理自定义事件

仅Adobe Experience Platform支持自定义事件。 自定义数据不会转发到Adobe Commerce功能板和量度跟踪器。

对于任意 `custom` 事件时，收集器会添加 `personId` (`ecid`) `customContext` 然后包裹 `xdm` 对象，然后再转发到Edge。

示例：

通过MSE SDK发布的自定义事件：

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

标准事件的属性覆盖仅支持Experience Platform。 自定义数据不会转发到商务功能板和量度跟踪器。

对于具有集的任何事件 `customContext`，则收集器会覆盖 `personId` 和Adobe Analytics计数器，并转发 `customContext`.

示例：

覆盖通过MSE SDK发布的产品视图：

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

具有Adobe Commerce的产品查看会覆盖通过MSE SDK发布的内容：

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
