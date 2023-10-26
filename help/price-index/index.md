---
title: SaaS价格索引
description: 使用SaaS价格索引提高性能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 3809d27fc3689519e4a162aa52f481d254aec656
workflow-type: tm+mt
source-wordcount: '713'
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

本小型指南介绍了SaaS价格索引的工作原理以及如何启用它。

## 要求

* Adobe Commerce 2.4.4+
* 使用最新版本的Adobe Commerce扩展时，请至少执行以下一个Commerce Services：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)
   * [产品Recommendations](../product-recommendations/guide-overview.md)

Luma和Adobe Commerce Core GraphQL用户可以安装 [`catalog-adapter`](catalog-adapter.md) 扩展可提供Luma和核心GraphQl兼容性并禁用Adobe Commerce产品价格索引器。

## 使用情况

升级具有SaaS价格索引支持的Adobe Commerce实例后，同步新的信息源：

```
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## 自定义产品类型的价格

自定义产品类型（如基本价格、特殊价格、组价格、目录规则价格等）支持价格计算。

如果您的自定义产品类型使用特定公式计算最终价格，则可以扩展产品价格信息源的行为。

## 使用情况

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

新馈送应手动与同步 `resync` [CLI命令](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 否则，数据将在标准同步过程中刷新。 获取有关 [目录同步](../landing/catalog-sync.md) 进程。

## 使用方案

### Luma没有扩展依赖关系

* 已安装所需服务(Live Search、Product Recommendations、Catalog Service)的Luma或Adobe Commerce Core GraphQL商家
* 没有依赖于PHP核心价格索引器的第三方扩展
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新馈送。
1. 安装目录适配器。

### 带有PHP核心价格索引器依赖项的Luma和Adobe Commerce核心GraphQl

* 已安装支持服务(Live Search、Product Recommendations、Catalog Service)的Luma或Adobe Commerce Core GraphQL商家
* 通过依赖于PHP核心价格索引器的第三方扩展
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源
1. 安装目录适配器。
1. 重新启用PHP核心价格索引器。
1. 在中使用新馈送和Luma兼容性代码 `catalog-adapter` 模块。

### Headless商家

* 已安装支持服务(Live Search、产品Recommendations、目录服务)的Headless商家
* 不依赖PHP核心价格索引器
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源
1. 安装目录适配器，该适配器将禁用PHP核心价格索引器。

## 自定义价格

SaaS价格索引器支持Adobe Commerce中提供的自定义产品类型价格功能，例如特殊价格、组价格和目录规则价格。

例如：存在自定义产品类型  `custom_type` 以及具有SKU“自定义类型产品”的产品。

默认情况下，Commerce Data Export扩展将以下价格信息源发送到价格索引器：

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

如果“自定义产品类型”使用唯一的公式来计算产品价格，则系统集成商可以通过扩展Commerce Data Export扩展来覆盖价格和折扣字段。

1. 在上创建插件 `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` 类。

`di.xml` 文件：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
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
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
