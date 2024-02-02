---
title: 收集数据
description: 了解事件如何收集产品推荐的数据。
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 7ed9321a2f4e58a7476aa91e74611fe896e1a7b1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 收集数据

安装和配置基于SaaS的Adobe Commerce功能时，例如 [产品Recommendations](install-configure.md) 或 [实时搜索](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)，模块会将行为数据收集部署到您的店面。 此机制从购物者那里收集匿名处理的行为数据并支持产品推荐。 例如， `view` 事件用于计算 `Viewed this, viewed that` 推荐类型和 `place-order` 事件用于计算 `Bought this, bought that` 推荐类型。

>[!NOTE]
>
>为产品推荐目的而收集的数据不包括个人身份信息(PII)。 所有用户标识符（如Cookie ID和IP地址）都经过严格匿名处理。 学习 [更多](https://www.adobe.com/privacy/experience-cloud.html).

以下事件并非特定于产品Recommendations，而是返回结果所必需的：

- `view`
- `add-to-cart`
- `place-order`

此 [Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) 列出部署到您的店面的所有事件。 但是，从该列表中，有一个特定于产品Recommendations的事件子集。 当购物者与店面上的推荐单元进行交互时，这些事件会收集数据，并增强用于帮助您分析推荐表现情况的量度。

| 事件 | 描述 | 是否用于指标？ |
| --- | --- | --- |
| `impression-render` | 推荐单元在页面上呈现。 | 是 |
| `rec-add-to-cart-click` | 客户单击 **添加到购物车** 推荐单位中项目的按钮。 | 是，当 **添加到购物车** “推荐”模板中存在按钮。 |
| `rec-click` | 客户单击推荐单位中的产品。 | 是 |
| `view` | 推荐单元将变为可在页面上查看，例如通过滚动到视图中。 | 是 |

要正确填充仪表板，需要以下事件。
| “仪表板”列 | 活动 | 加入字段 | | ---------------- | --------- | ----------- | | 展示次数 |`page-view`， `recs-request-sent`， `recs-response-received`， `recs-unit-render` | unitId | | 视图 |`page-view`， `recs-request-sent`， `recs-response-received`， `recs-unit-render`， `recs-unit-view` | unitId | | 点击次数 |`page-view`， `recs-request-sent`， `recs-response-received`， `recs-item-click`， `recs-add-to-cart-click`    | unitId | | 收入 |`page-view`， `recs-request-sent`， `recs-response-received`， `recs-item-click`， `recs-add-to-cart-click`， `place-order` | unitId， sku | | LT收入 |`page-view`， `recs-request-sent`， `recs-response-received`， `recs-item-click`， `recs-add-to-cart-click`， `place-order` | unitId， sku | | CTR |`page-view`， `recs-request-sent`， `recs-response-received`， `recs-unit-render`， `recs-item-click`， `recs-add-to-cart-click`  | unitId， sku | | vCTR |`page-view`， `recs-request-sent`， `recs-response-received`， `recs-unit-render`， `recs-unit-view`， `recs-item-click`， `recs-add-to-cart-click` | unitId， sku |

如果您的店面采用PWA Studio实施，请参阅 [PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自定义前端技术，例如React或Vue JS，请参阅用户指南以了解如何集成 [Headless中的产品Recommendations](headless.md) 环境。

## 注意事项

广告拦截器和隐私设置可阻止 `magento/product-recommendations` 模块捕获事件，这可能会导致参与和收入 [量度](workspace.md) 被少报。

事件不会捕获商户网站上发生的每个交易。 事件旨在让商家大致了解网站上发生的事件。

Headless实施必须实施事件以支持Product Recommendations功能板。

>[!NOTE]
>
>如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 启用，在购物者同意使用Cookie之前，Adobe Commerce不会收集行为数据。 如果“Cookie限制模式”被禁用，Adobe Commerce会默认收集行为数据。
