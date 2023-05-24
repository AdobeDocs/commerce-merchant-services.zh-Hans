---
title: 收集数据
description: 了解事件如何收集产品推荐的数据。
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 收集数据

安装和配置基于SaaS的Adobe Commerce功能时，例如 [产品Recommendations](install-configure.md) 或 [实时搜索](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)，模块会将行为数据收集部署到您的店面。 此机制从购物者那里收集匿名行为数据并支持产品推荐。 例如， `view` 事件用于计算 `Viewed this, viewed that` 推荐类型，以及 `place-order` 事件用于计算 `Bought this, bought that` 推荐类型。

>[!NOTE]
>
>为产品推荐目的收集的数据不包括个人身份信息(PII)。 所有用户标识符（如Cookie ID和IP地址）都经过严格匿名处理。 [了解详情](https://www.adobe.com/privacy/experience-cloud.html).

以下事件并非特定于产品Recommendations，而是返回结果所必需的：

- `view`
- `add-to-cart`
- `place-order`

此 [Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) 列出部署到您的店面的所有事件。 但是，从该列表中，有一个特定于产品Recommendations的事件子集。 当购物者与店面的推荐单位进行交互时，这些事件会收集数据，并增强用于帮助您分析推荐表现情况的量度。

| 事件 | 描述 | [是否用于指标？](workspace.md) |
| --- | --- | --- |
| `impression-render` | 推荐单元呈现在页面上。 | 是 |
| `rec-add-to-cart-click` | 客户单击 **添加到购物车** 推荐单位中项目的按钮。 | 是，当 **添加到购物车** 按钮显示在推荐模板中。 |
| `rec-click` | 客户单击推荐单位中的产品。 | 是 |
| `view` | 推荐单元在页面上变为可见，例如通过滚动到视图中。 | 是 |

如果您的店面采用PWA Studio实施，请参阅 [PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自定义前端技术（如React或Vue JS），请参阅用户指南，了解如何在中集成产品Recommendations [headless](headless.md) 环境。

## 注意事项

广告拦截器和隐私设置可以阻止 `magento/product-recommendations` 模块捕获事件，这可能会导致参与度和收入 [量度](workspace.md) 被少报。

事件不会捕获商户网站上发生的每个交易。 事件旨在让商家大致了解网站上发生的事件。

Headless实施必须实施事件以支持Product Recommendations功能板。

>[!NOTE]
>
>如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 启用，在购物者同意使用Cookie之前，Adobe Commerce不会收集行为数据。 如果禁用了Cookie限制模式，Adobe Commerce会默认收集行为数据。
