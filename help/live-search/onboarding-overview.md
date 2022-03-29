---
title: 入门概述
description: 实时搜索入门流程、系统要求、边界和限制
source-git-commit: 6220824c6032a33a760fe5c2bb5d2346e00a074b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 入门概述

要开始使用Adobe Commerce的实时搜索，您必须完成一些入门步骤以安装扩展、配置API密钥和同步目录。

## 载入流程

![实时搜索载入图](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* 7.3菲律宾比索/7.4
* [!DNL Composer]

### 支持的平台

* Adobe Commerce on prem(EE):2.4.x
* Adobe Commerce on Cloud(ECE):2.4.x

## 边界和阈值

目前，实时搜索/类别API具有以下受支持的限制和静态边界：

### 索引

* 每个商店视图最多可为300个产品属性建立索引
* 仅对Adobe Commerce数据库中的产品进行索引
* 不为CMS页面编入索引

### 查询限制

* 实时搜索无权访问类别树的完整分类，这会导致某些分层导航搜索方案超出其覆盖范围。
* 实时搜索使用唯一的GraphQL端点进行查询，以支持智能分面和按类型搜索等功能。 尽管与 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)，则存在一些差异，某些字段当前可能不完全兼容。

### PWA测试版

* 实时搜索PWA测试版不支持 [事件处理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* 与的测试版相关联使用时，GraphQL不支持以下产品属性 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 当前不支持

* 的 [高级搜索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 安装实时搜索时，模块会被禁用，并且会删除店面页脚中的“高级搜索”链接。
* [客户群组](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [自定义价格组](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* 使用的多个库存位置 [MCOM](https://docs.magento.com/user-guide/mcom.html) 或其他OMS扩展
* [集成的B2B功能](https://business.adobe.com/products/magento/b2b-ecommerce.html)
