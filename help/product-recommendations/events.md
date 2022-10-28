---
title: 收集数据
description: 了解事件如何收集产品推荐的数据。
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 收集数据

安装和配置基于SaaS的Adobe Commerce功能(例如 [产品Recommendations](install-configure.md) 或 [实时搜索](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)，则模块会将行为数据收集部署到您的店面。 此机制从购物者那里收集匿名化行为数据，并为产品推荐提供支持。 例如， `view` 事件用于计算 `Viewed this, viewed that` 推荐类型和 `place-order` 事件用于计算 `Bought this, bought that` 推荐类型。

>[!NOTE]
>
>为产品推荐目的收集的数据不包括个人身份信息(PII)。 所有用户标识符（如Cookie ID和IP地址）都严格匿名化。 [了解更多](https://www.adobe.com/privacy/experience-cloud.html).

以下事件并非特定于产品Recommendations，而是返回结果所必需的：

- `view`
- `add-to-cart`
- `place-order`

的 [Adobe Commerce Storefront事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) 列出部署到店面的所有事件。 但是，该列表中存在特定于产品Recommendations的事件子集。 当购物者与店面上的推荐单位进行交互时，这些事件会收集数据，并为用来帮助您分析推荐效果的量度提供动力。

| Event | 描述 | [用于量度？](workspace.md) |
| --- | --- | --- |
| `impression-render` | 推荐单元呈现在页面上。 | 是 |
| `rec-add-to-cart-click` | 客户单击 **添加到购物车** 按钮。 | 是，当 **添加到购物车** 按钮。 |
| `rec-click` | 客户在推荐单位中单击产品。 | 是 |
| `view` | 推荐单元可在页面上查看，例如通过滚动到视图中。 | 是 |

如果您的店面是通过PWA Studio实施的，请参阅 [PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自定义前端技术（如React或Vue JS），请参阅用户指南，以了解如何在 [无头](headless.md) 环境。

广告阻止程序和隐私设置可能会阻止 `magento/product-recommendations` 模块来捕获事件，并可能导致参与和收入 [量度](workspace.md) 少报。

>[!NOTE]
>
>如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 启用，则在购物者同意使用cookie之前，Adobe Commerce不会收集行为数据。 如果禁用Cookie限制模式，则Adobe Commerce会默认收集行为数据。
