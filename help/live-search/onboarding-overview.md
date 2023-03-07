---
title: “入门培训概述”
description: ”[!DNL Live Search] 载入流程、系统要求、边界和限制”
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# 载入概述

开始使用 [!DNL Live Search] 对于Adobe Commerce，请完成入门培训过程以安装扩展，配置API密钥，并同步目录。

## 载入流程

![[!DNL Live Search] 载入流程图](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.4+
* PHP 8.1、8.2
* [!DNL Composer]

### 支持的平台

* 本地Adobe Commerce (EE) ：2.4.4+
* Adobe Commerce on Cloud (ECE) ：2.4.4+

## 边界和阈值

此时， [!DNL Live Search] 搜索/类别API具有以下支持的限制和静态边界：

### 索引

* 每个存储视图最多索引300个产品属性。
* 仅对Adobe Commerce数据库中的产品编制索引。
* CMS页面未索引。

### 查询

* [!DNL Live Search] 无权访问类别树的完整分类，这使得一些分层导航搜索场景超出其范围。
* [!DNL Live Search] 使用查询的唯一GraphQL端点来支持智能彩块化和按类型搜索等功能。 尽管与 [MAGENTOGRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)存在一些差异，一些字段当前可能不完全兼容。

### 规则

* 每个存储视图的最大规则数为50。
* 每个规则的最大条件数为10。
* 每个规则的最大事件数为25。

### 同义词

* [!DNL Live Search] 每个存储视图最多可管理200个同义词。

### PWA测试版

* 与使用本机Commerce店面的实时搜索相比，实时搜索的当前测试版PWA实施需要更多处理时间来返回搜索结果。
* 的PWA测试版 [!DNL Live Search] 不支持 [事件处理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 以下产品属性在与Beta版一起使用时未受到GraphQL的支持 [PWA](https://developer.adobe.com/commerce/pwa-studio/)： `description`， `name`， `short_description`

### 目前不支持

* 此 [高级搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 在以下情况下禁用模块： [!DNL Live Search] ，并删除店面页脚中的高级搜索链接。
* [自定义价格组](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* 由使用的多个库存库位 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS扩展
* 产品价格不包括 [增值税](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) （增值税）。
