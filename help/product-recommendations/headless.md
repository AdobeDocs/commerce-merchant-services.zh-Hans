---
title: 无头
description: 了解如何集成 [!DNL Product Recommendations] 在无头店里。
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 无头

您可以集成 [!DNL Product Recommendations] 在无头店面中使用 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 或自定义前端技术，如React或Vue JS。

[!DNL Product Recommendations] 要求 [行为和目录数据](https://devdocs.magento.com/recommendations/product-recs.html#typesofdata) 操作。 目录数据同步过程在无标题实施中保持不变，但行为数据收集需要进行更改。

集成 [!DNL Product Recommendations] 在无头店，您必须：

1. 将行为数据发送到Adobe Sensei以分析和计算产品推荐结果。 您还可以发送其他数据以启用产品推荐 [量度报告](workspace.md).

1. 获取产品推荐结果并在页面上渲染这些结果。

您可以按照以下工作流中所述，使用可用的SDK执行这两个操作。

1. [安装](install-configure.md) the [!DNL Product Recommendations] 模块。

1. 安装和使用 [Storefront事件SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) 来发火 [行为事件](https://devdocs.magento.com/recommendations/events.html).

   需要返回的最小事件数 [!DNL Product Recommendations] 结果：

   | Event | 类别 |
   |--- | ---|
   | `view` | 产品 |
   | `add-to-cart` | 产品 |
   | `place-order` | 结账 |

   启用 [量度报告](workspace.md)，则需要以下其他事件：

   | 事件 | 类别 |
   |--- | ---|
   | `impression-render` | 推荐单元 |
   | `view` | 推荐单元 |
   | `rec-click` | 推荐单元 |
   | `rec-add-to-cart-click` | recommendations-unit（如果“推荐”模板中存在“添加到购物车”按钮） |

1. 触发事件时，使用 [Storefront事件收集器](https://devdocs.magento.com/shared-services/storefront-event-collector.html) 来处理事件，并将其发送到Adobe Sensei。

1. 收集行为数据后，您可以 [创建](create.md) [!DNL Product Recommendations] 中。

1. 使用 [Recommendations SDK](https://devdocs.magento.com/recommendations/recs-api.html) 以获取店面上的推荐单位。 SDK会返回在页面上呈现推荐单元所必需的产品数据。
