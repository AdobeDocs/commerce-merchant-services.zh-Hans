---
title: 自定义
description: 了解如何自定义产品推荐。
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: a34c3c8a5caca1bbf611b2df650c562aeeab297b
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---

# 自定义

安装产品Recommendations模块时，Adobe Commerce将创建 `ProductRecommendationsLayout` 目录访问Advertising Cloud的帮助。 此目录包含可自定义以更改推荐在店面上显示方式的模板文件。 具体而言，您可以修改或覆盖以下模板：

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

有关修改模板文件的更多信息，请参阅 [模板自定义](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) （在Frontend开发人员指南中）。

如果您修改 `recommendations.html` 文件中，您必须在文件中保留以下标记，以确保Adobe Commerce可以从您的店面收集推荐量度：

| 标记 | 使用 |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | 收集视图事件。 |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | 收集点击事件。 <br/>**注意：** 如果添加任何锚点标记，则必须包含这些属性。 |

除 `recommendations.html` 文件， `ProductRecommendationsLayout` 目录包含以下子目录：

| 目录 | 用途 |
|---|---|
| `layout` | 包含 `*.xml` 每个页面类型的文件 |
| `templates` | 包含调用获取和渲染脚本的文件 |
| `web/js` | 包含用于获取和渲染存储推荐的JavaScript文件 |
| `web/template` | 包含的模板 `magento/product-recommendations` 模块 |

## 推荐单元定位

当您 [创建](create.md) 推荐，则需指定 [位置](placement.md) 页面上显示的位置。 推荐单元可以放置在主内容容器的顶部或底部。 但是，您可以自定义此版面。 如果创建Page Builder推荐内容类型，请使用Page Builder工具将推荐单元放置在页面上。 对于所有其他页面类型，请编辑 `*.xml` 创建推荐时生成的文件。

1. 更改为 `layout` 目录：

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   下表列出了此目录中存在的XML文件：

   | 文件名 | 页面 |
   |---|---|
   | `catalog_category_view.xml` | 类别 |
   | `catalog_product_view.xml` | 产品详细信息 |
   | `checkout_cart_index.xml` | 购物车 |
   | `checkout_onepage_success.xml` | 结帐 |
   | `cms_index_index.xml` | 主页 |

   >[!NOTE]
   >
   >文件名位于 `layout` 如果您的存储使用第三方扩展，则目录可能会不同。

1. 让我们修改 `catalog_product_view.xml` 文件，以便推荐单元显示在产品详细信息页面上的产品图像之后。 在自定义此XML文件之前，让我们先看看该文件，并了解需要修改的部分：

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   在上述代码片段中， `main.content` 引用块指示推荐单元将放置在相对于该元素的某个位置。 其 `block` 元素包含 `after="-"` 属性，该属性指定将在主内容块之后的页面上显示推荐单元。

1. 让我们通过指定其他内容块来修改此文件。

   您将更改引用块 `name` 从 `main.content` to `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   此更改会导致推荐单元显示在产品详细信息页面上的产品图像之后。 如果您希望推荐单元显示在 `product.info.media`，请更改 `after="-"` 属性 `before="-"`. 的 `pagePlacement` 参数是不应修改的内部参数。

请参阅 [布局概述](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) 以了解有关页面上块类型的更多信息。

## 自定义产品属性

开发人员通常需要访问店面推荐单元中的自定义产品属性值，以便他们能够根据这些属性为产品添加视觉处理。

例如，如果您的商店销售一些有机产品，则可能在那些将其指定为 `Organic = Yes`. 您可能需要在店面上访问此属性值，以便在这些产品出现在Recommendations中时对这些产品给予特殊的视觉处理。 同样，通过访问这些自定义产品属性值，您可以在网站的表示层标记产品或驱动自定义逻辑。

![添加标记](assets/unit-custom.png)

要确保在页面上呈现推荐单元时自定义产品属性可用，请将 `Used in Product Listing` 属性 `Yes` 在 [产品属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) 页面。

设置此属性后，JSON有效负载将包含 `attributes` 包含属性代码和值数组的对象。 然后，您可以根据这些属性值应用自定义店面样式，例如，添加如前所述的特殊视觉处理或徽章。

>[!NOTE]
>
>产品属性更改可能最多需要一小时才能显示在JSON有效负载中。
