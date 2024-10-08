---
title: 扩展和自定义SaaS数据导出馈送数据
description: 了解如何扩展和自定义 [!DNL SaaS Data Export] 馈送数据。
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 扩展和自定义SaaS数据导出馈送数据

[!DNL Commerce Data Export]扩展提供了一种将数据从[!DNL Commerce]应用程序导出到Commerce服务(如Live Search、目录服务和产品Recommendations)的方法。 如果需要，您可以扩展和自定义馈送数据以包含其他数据，或通过更新`Magento\CatalogDataExporter`模块来修改收集的数据。

>[!NOTE]
>
>向馈送添加新数据或修改现有数据可能会影响馈送收集性能，并导致Adobe Commerce端的处理逻辑出现问题。 在合并到生产环境之前，请务必测试自定义的代码。

## 扩展产品信息源中的属性数据

产品信息源包含产品处理所需的或消费者常用的默认属性。 通过将其他系统属性添加到产品信息源，您可以在产品信息源中包含这些属性。

要完成此任务，请更新`magento/catalog-data-exporter`模块以将其他系统属性添加到[依赖项注入配置文件](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`)。 将属性添加到产品属性查询(`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`)。

**示例**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
