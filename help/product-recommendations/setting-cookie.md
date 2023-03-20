---
title: 处理Cookie限制
description: 了解产品推荐如何处理Cookie限制。
exl-id: 2f48c47c-569b-455c-a589-8f99b7b74064
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# 处理Cookie限制

在将数据存储到浏览器Cookie中之前，Adobe Commerce和Magento Open Source都会请求获取同意。 有关更多信息，请参阅 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

当您部署 `magento/product-recommendations` 模块到生产环境，它会开始收集您店面上的购物者交互事件。 由于这些事件的数据可以存储在浏览器Cookie或本地存储中，因此该功能支持Cookie限制模式，具体方法是在购物者获得Cookie同意之前不收集事件。

这可能不适用于第三方Cookie同意解决方案。 每家商户均有责任确保在获得Cookie同意之前（通常是法律要求的）不会进行数据收集。 如果您使用自定义代码管理Cookie同意，则可以使用名为的do-not-track Cookie `mg_dnt` 来限制数据收集。

- Cookie的名称：

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- 设置do-not-track Cookie以禁用数据收集：

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- 要在用户接受Cookie时清除Cookie，请执行以下操作：

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
