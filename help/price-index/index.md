---
title: SaaS价格索引
description: 使用SaaS价格索引提高性能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 92129633adadd3ed699ae6427c01622dcb6ae3b4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# SaaS价格索引

SaaS价格指数缩短了反映价格变化所需的时间 [Commerce服务](../landing/saas.md) 在提交之后。 这允许拥有大型复杂目录或具有多个网站或客户组的商家持续处理价格变化。
如果您有Headless店面或使用 [catalog-adapter](./catalog-adapter.md) 扩展后，客户可以禁用Adobe Commerce核心价格索引器。

计算密集型流程（如索引和价格计算）已从Commerce核心转移到Adobe的云基础架构。 这使商家能够快速扩展资源以缩短价格指数化时间，并更快地反映这些变化。

核心索引数据流向SaaS服务的形式如下所示：

![默认数据流](assets/old_way.png)

使用SaaS价格指数时，流程是：

![SaaS价格索引数据流](assets/new_way.png)

所有商家都可以从这些改进中受益，但收益最大的是以下客户：

* 价格持续变化：商家需要重复更改价格以满足战略目标，如频繁促销、季节性折扣或库存减价。
* 多个网站和/或客户组：在多个网站（域/品牌）和/或客户组之间共享产品目录的商家。
* 跨网站或客户组的大量唯一价格：具有大量共享产品目录（包含跨网站或客户组的唯一价格）的商家，例如，具有预先协商价格的B2B商家，以及具有不同定价策略的品牌。

使用Adobe Commerce服务的客户可以免费获取SaaS价格索引，并支持计算所有内置Adobe Commerce产品类型的价格。

本指南介绍SaaS价格索引的工作原理以及如何启用它。

## 要求

* Adobe Commerce 2.4.4+
* 使用最新版本的Adobe Commerce扩展时，请至少执行以下一个Commerce Services：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)

Luma和Adobe Commerce Core GraphQL用户可以安装 [`catalog-adapter`](catalog-adapter.md) 扩展可提供Luma和核心GraphQl兼容性并禁用Adobe Commerce产品价格索引器。

## 使用情况

升级具有SaaS价格索引支持的Adobe Commerce实例后，同步新的信息源：

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## 自定义产品类型的价格

自定义产品类型（如基本价格、特殊价格、组价格、目录规则价格等）支持价格计算。

如果您的自定义产品类型使用特定公式计算最终价格，则可以扩展产品价格信息源的行为。

1. 在上创建插件 `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` 类。

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
       </type>
   </config>
   ```

1. 使用自定义公式创建方法：

   ```php
   class UpdatePriceFromFeed
   {
       /**
       * @param ProductPrice $subject
       * @param array $result
       * @param array $values
       *
       * @return array
       */
       public function afterGet(ProductPrice $subject, array $result, array $values) : array
       {
           // Override the output $result with your data for the corresponding products (see original method for details) 
           return $result;
       }
   }
   ```
