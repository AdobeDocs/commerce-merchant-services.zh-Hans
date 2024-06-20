---
title: "[!DNL Storefront Popover]"
description: “ [!DNL Live Search storefront popover] 会动态返回建议的产品和缩略图。”
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Storefront Popover]

时间 [!DNL Live Search] 是 [已安装](install.md)， a [!DNL popover] 出现在店面时，购物者键入 [Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 盒子。 键入每个字符后， [!DNL popover] 将更新为推荐的产品和排名最前的搜索结果的缩略图图像。

[!DNL Live Search] 返回两个字符或更多字符的查询结果。 对于部分匹配，每个单词的最大字符数为20。 “键入时搜索”查询中的字符数无法配置。

默认情况下， [!DNL Live Search] 支持 [搜索词重定向](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>了解如何在中将产品属性设置为可搜索 [设置Live Search](workspace.md) 文章。

## [!DNL Popover] 页面大小

的页面大小 [!DNL popover] 确定可以返回多少行自动完成产品。 在Live Search安装过程中， `page_size` 的值将更改为的当前 [目录搜索](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 设置。

默认情况下，“目录搜索 — 自动完成限制”值设置为八行。 要更改 [!DNL popover]，请执行以下操作：

1. 在 *管理员* 侧栏，转到 **商店** >设置> **配置**.
1. 在左侧面板中，展开 **目录** 并选择 **目录** 从设置列表中。
1. 展开 *目录搜索* 部分。
1. 设置 **自动完成限制** 到您希望在 [!DNL popover].
1. 完成后，单击 **保存配置**.

## 样式 [!DNL Popover] 示例

您可以自定义 [!DNL Popover] 小部件，以符合贵公司的风格和品牌指南。

此 [!DNL storefront popover] 始终显示产品 `name` 和 `price`，并且无法配置字段选择。 但是， [!DNL popover] 可以使用为元素设置样式 [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) 类。 例如，以下声明更改了 [!DNL popover] 容器和页脚。

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## 容器可见性

的父组件 `.livesearch.popover-container` 是 `.search-autocomplete`.  此 `.active` 类指示容器的可见性。 此 `.active` 类有条件地添加当 [!DNL popover] 是打开的。

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

有关设置店面元素样式的详细信息，请参阅 [层叠样式表(CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) 在 [前端开发人员指南](https://developer.adobe.com/commerce/frontend-core/guide/).

## 类选择器

您可以使用以下类选择器来设置容器和产品元素在 [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

### 容器类选择器

#### .livesearch.pover-container

![[!DNL Popover] 容器](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![查看所有页脚](assets/livesearch-view-all-footer.png)

### 产品类选择器

#### .livesearch.products-container

![产品容器](assets/livesearch-product-container.png)

#### .livesearch.product-result

![产品结果](assets/livesearch-product-result.png)

#### .livesearch.product-name

![产品名称](assets/livesearch-product-name.png)

#### .livesearch.product-price

![产品价格](assets/livesearch-product-price.png)

#### .livesearch产品链接

![产品结果](assets/livesearch-product-link.png)

## 使用修改的主题 {#working-with-modified-theme}

您可以使用 [!DNL storefront popover] 带有自定义 [主题](https://developer.adobe.com/commerce/frontend-core/guide/themes/) 所需的文件继承自 *Luma*. 此 `top.search` 中的块 `header-wrapper` 的 `Magento_Search` 不得修改模块。

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## 禁用 [!DNL popover]

要禁用 [!DNL popover] 并恢复标准 [快速搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 功能，输入以下命令：

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```

## Headless实施

对于采用Headless实施的客户，您可以安装 [!DNL Live Search popover] 使用 [npm包](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
