---
title: 验证事件集合
description: 了解如何验证行为数据是否被发送到Adobe Commerce。
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 验证事件集合

在 [安装和配置](install-configure.md) the `magento/product-recommendations` 模块中，您可以验证行为数据是否已发送到Adobe Commerce。 您可以使用Chrome中提供的开发人员工具，或安装Snowploogh Chrome扩展。 如果您需要其他帮助，请参阅 [故障诊断 [!DNL Product Recommendations] 模块](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 在支持知识库中。

## 在Chrome中使用开发人员工具进行验证

要确保在所有网站页面上加载事件收集器JS文件，请执行以下操作：

1. 在Chrome中，选择 **自定义和控制Google Chrome** 然后选择 **更多工具** > **开发人员工具**.
1. 选择 **网络** ，然后选择 **JS** 类型。
1. 筛选 `ds.`
1. 重新加载页面。
1. 您应会看到 `ds.js` 或 `ds.min.js` 在 **名称** 列。

![事件收集器JS](assets/filter-ds.png)
_事件收集器JS_

要确保事件在您网站的页面（主页、产品、结帐等）上触发，请执行以下操作：

1. 确保禁用浏览器上的任何广告拦截器，并接受网站上的Cookie。
1. 在Chrome中，选择 **自定义和控制Google Chrome** （浏览器右上角的三个垂直圆点），然后选择 **更多工具** > **开发人员工具**.
1. 选择 **网络** 选项卡和过滤器 `tp2`.
1. 重新加载页面。
1. 您应会在下方看到调用 `tp2` 在 **名称** 列。

![触发事件](assets/filter-tp2.png)
_验证事件是否触发_

## 使用Snowploogh Chrome扩展进行验证

安装 [适用于Chrome的Snowploogh Analytics Debugger扩展](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). 此扩展显示收集到的事件并将其发送到Adobe Commerce。

1. 确保禁用浏览器上的任何广告拦截器，并接受网站上的Cookie。

1. 在Chrome中，选择 **自定义和控制Google Chrome** （浏览器右上角的三个垂直圆点），然后选择 **更多工具** > **开发人员工具**.

1. 选择 **Snowplough Analytics调试器** 选项卡。

1. 在 **事件** 列，选择 **结构化事件**.

1. 向下滚动直到您看到 **上下文数据 _n_**. 在&#x200B;**架构**.

1. 验证 [SaaS数据空间ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 设置正确。

![雪犁过滤器](assets/snowplow-filter.png)
_雪犁过滤器_

>[!NOTE]
>
> 值 `Data validity : NOT FOUND` 调试器中的调试器指示内部架构。 Snowplough Chrome插件无法使用内部架构验证事件。 这对实际功能没有影响。

## 验证事件是否正确触发

要验证用于量度的事件是否正确触发，请查找 `impression-render`, `view`和 `rec-click` Snowplough Analytics Debugger中的事件。 请参阅 [事件的完整列表](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> 如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 启用，则Adobe Commerce在购物者同意之前不会收集行为数据。 如果禁用Cookie限制模式，则默认情况下会收集行为数据。
