---
title: 入门概述
description: 实时搜索入门流程、系统要求、边界和限制
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: f2934746c327528d5d52f2ae356afe303ff9b81b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 入门概述

开始使用 [!DNL Live Search] 对于Adobe Commerce，请完成载入过程以安装扩展、配置API密钥并同步目录。

## 载入流程

![[!DNL Live Search] 载入图](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### 支持的平台

* Adobe Commerce on prem(EE):2.4.x
* Adobe Commerce on Cloud(ECE):2.4.x

## 边界和阈值

此时， [!DNL Live Search] 搜索/类别API具有以下受支持的限制和静态边界：

### 索引

* 每个商店视图最多可为300个产品属性建立索引
* 仅对Adobe Commerce数据库中的产品进行索引
* 不为CMS页面编入索引

### 查询限制

* [!DNL Live Search] 无权访问类别树的完整分类，这会导致某些分层导航搜索方案超出其覆盖范围。
* [!DNL Live Search] 对查询使用唯一的GraphQL端点来支持智能分面和按类型搜索等功能。 尽管与 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)，则存在一些差异，某些字段当前可能不完全兼容。

### PWA测试版

* 与使用本机Commerce店面的Live Search相比，当前Live Search测试版PWA实施需要更多的处理时间才能返回搜索结果。
* 测试版PWA [!DNL Live Search] 不支持 [事件处理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* 与的测试版相关联使用时，GraphQL不支持以下产品属性 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 当前不支持

* 的 [高级搜索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 模块在 [!DNL Live Search] ，并且会删除店面页脚中的高级搜索链接。
* [客户群组](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [自定义价格组](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* 使用的多个库存位置 [MCOM](https://docs.magento.com/user-guide/mcom.html) 或其他OMS扩展
* [集成的B2B功能](https://business.adobe.com/products/magento/b2b-ecommerce.html)
* 产品价格不包括 [增值税](https://docs.magento.com/user-guide/tax/vat.html) （增值税）。
* 无现货产品会显示在搜索结果中，与 [股票期权](https://docs.magento.com/user-guide/catalog/inventory-options-global.html) 配置。
