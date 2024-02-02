---
title: ’[!DNL Live Search] 事件
description: 了解事件如何收集以下项的数据 [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 8d669cf6042340659574c86a43836a02954f24ce
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# [!DNL Live Search] 活动

[!DNL Live Search] 使用事件增强搜索算法，例如“查看次数最多”和“查看了这个项目，查看了那个项目”。 虽然LUMA用户可开箱即用地实施事件，但Headless和其他自定义实施必须实施事件以满足其自身需求。

从 [!DNL Live Search] 和 [!DNL Product Recommendations] 使用相同的后端算法，某些事件由两个服务共享。 需要一些产品Recommendations事件才能填充Recommendations功能板。

## 活动

此表介绍了使用的事件 [!DNL Live Search] 策略。

| 策略 | 产品 | 活动 | 页面 |
| --- | --- | --- | ---|
| 查看次数最多 | 实时搜索<br>产品推荐 | 页面查看<br>产品查看 | 产品详细信息页面 |
| 购买次数最多 | 实时搜索<br>产品推荐 | 页面查看<br>完成签出 | 购物车/结帐 |
| 添加到购物车的次数最多 | 实时搜索<br>产品推荐 | 页面查看<br>添加到购物车 | 产品详细信息页面<br>产品列表页面<br>购物车<br>愿望清单 |
| 查看了这个项目，也查看了那个项目 | 实时搜索<br>产品推荐 | 页面查看<br>产品查看 | 产品详细信息页面 |
| 趋势 | 实时搜索<br>产品推荐 | 页面查看<br>产品查看 | 产品详细信息页面 |
| 查看了这个项目，购买了那个项目 | 产品推荐 | 页面查看<br>产品查看 | 产品详细信息页面<br>购物车/结帐 |
| 购买了此项，也购买了此项 | 产品推荐 | 页面查看<br>产品查看 | 产品详细信息页面 |
| 转化：查看以购买 | 产品推荐 | 页面查看<br>产品查看 | 产品详细信息页面 |
| 转化：查看以购买 | 产品推荐 | 页面查看<br>完成签出 | 购物车/结帐 |
| 转化：查看到购物车 | 产品推荐 | 页面查看<br>产品查看 | 产品详细信息页面 |
| 转化：查看到购物车 | 产品推荐 | 页面查看<br>添加到购物车 | 产品详细信息页面<br>产品列表页面<br>购物车<br>愿望清单 |

>[!NOTE]
>
>为以下目的收集数据 [!DNL Live Search] 不包括个人身份信息(PII)。 所有用户标识符（如Cookie ID和IP地址）都经过严格匿名处理。 [了解详情](https://www.adobe.com/privacy/experience-cloud.html).

## 必需的报告面板事件

需要使用某些事件来填充 [实时搜索功能板](performance.md)

| 仪表板区域 | 活动 | 加入字段 |
| ------------------- | ------------- | ---------- |
| 独特搜索 | `page-view`， `search-request-sent`， | searchRequestId |
| 零结果搜索 | `page-view`， `search-request-sent`， | searchRequestId |
| 零结果率 | `page-view`， `search-request-sent`， | searchRequestId |
| 热门搜索 | `page-view`， `search-request-sent`， | searchRequestId |
| 平均 点击位置 | `page-view`， `search-request-sent`， `search-response-received`， `search-results-view`， `search-product-click` | searchRequestId |
| 点进率 | `page-view`， `search-request-sent`， `search-response-received`， `search-results-view`， `search-product-click` | searchRequestId， sku |
| 转化率 | `page-view`， `search-request-sent`， `search-response-received`， `search-results-view`， `search-product-click`， `product-view`， `add-to-cart`， `place-order` | searchRequestId， sku |

### 所需上下文

所有事件都需要 `Page` 和 `Storefront` 上下文。 这应在页面级别/店面应用程序层发生，而不是在生成单个事件时发生（例如，在PHP店面中，PHP应用程序容器负责在运行时设置它们）。

## 使用情况

以下是 `search-request-sent` 事件：

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## 注意事项

广告拦截器和隐私设置可能会阻止捕获事件，并且可能会导致参与和收入 [量度](workspace.md) 少报。

事件不会捕获商户网站上发生的每个交易。 事件旨在让商家大致了解网站上发生的事件。

Headless实施必须实施事件以支持 [产品Recommendations功能板](../product-recommendations/events.md).

>[!NOTE]
>
>如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 启用，在购物者同意使用Cookie之前，Adobe Commerce不会收集行为数据。 如果“Cookie限制模式”被禁用，Adobe Commerce会默认收集行为数据。
