---
title: Headless
description: 了解如何集成 [!DNL Product Recommendations] 在headless店面。
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Headless

您可以集成 [!DNL Product Recommendations] 在headless店面中使用 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 或自定义前端技术，例如React或Vue JS。

自定义和Headless集成商应该参考这些Luma和PWA说明作为建议的实施。 可通过多种方法将产品Recommendations实施到Headless解决方案中，本文档并未涵盖所有场景。 集成商必须为其实施提供事件、设计和测试服务。

[!DNL Product Recommendations] 需要 [行为和目录数据](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) 来操作。 在Headless实施中，目录数据同步过程保持不变，但行为数据收集需要更改。

>[!NOTE]
>
>Headless实例必须实施事件以支持Product Recommendations功能板。

要集成 [!DNL Product Recommendations] 在headless店面，您必须：

1. 将行为数据发送到Adobe Sensei以分析和计算产品推荐结果。 您还可以发送其他数据以启用产品推荐 [量度报告](workspace.md).

1. 获取产品推荐结果并在页面上呈现这些结果。

您可以使用可用的SDK执行这两项操作，如下面的工作流中所述。

1. [安装](install-configure.md) 此 [!DNL Product Recommendations] 模块。

1. 安装并使用 [Adobe Commerce店面活动SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 以触发 [行为事件](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   要返回的最小所需事件 [!DNL Product Recommendations] 结果：

   | 事件 | 类别 |
   |--- | ---|
   | `view` | product |
   | `add-to-cart` | product |
   | `place-order` | 结账 |

   启用 [量度报告](workspace.md)，则需要以下附加事件：

   | 事件 | 类别 |
   |--- | ---|
   | `impression-render` | 推荐单位 |
   | `view` | 推荐单位 |
   | `rec-click` | 推荐单位 |
   | `rec-add-to-cart-click` | 推荐单位（如果推荐模板中存在“添加到购物车”按钮） |

1. 触发事件时，使用 [Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) 以处理事件并将它们发送到Adobe Sensei。

1. 收集行为数据后，您可以 [创建](create.md) [!DNL Product Recommendations] 在Admin中。

1. 使用 [RECOMMENDATIONS SDK](https://developer.adobe.com/commerce/services/product-recommendations/) 获取店面上的推荐单位。 SDK会返回必要的产品数据以呈现页面上的推荐单元。
