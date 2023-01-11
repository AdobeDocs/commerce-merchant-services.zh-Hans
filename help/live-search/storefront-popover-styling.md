---
title: “样式 [!DNL Popover] 元素”
description: “关于自定义 [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 样式 [!DNL Popover] 元素

的 [[!DNL storefront popover]](storefront-popover.md) 始终显示产品 `name` 和 `price`，且无法配置字段的选择。 但是， [!DNL popover] 元素可以使用CSS类设置样式。 例如，以下声明会更改 [!DNL popover] 容器和页脚。

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## 容器可见性

的父组件 `.livesearch.popover-container` is `.search-autocomplete`.  的 `.active` 类表示容器的可见性。 的 `.active` 当 [!DNL popover] 打开。

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

有关店面元素样式的更多信息，请参阅 [层叠样式表(CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) 在 [Frontend开发人员指南](https://developer.adobe.com/commerce/frontend-core/guide/).

## 类选择器

以下类选择器可用于设置 [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### 容器类选择器

#### .livesearch.popover-container

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

## 使用修改的主题 {#working-with-modified-theme}

的 [!DNL storefront popover] 可与自定义 [主题](https://developer.adobe.com/commerce/frontend-core/guide/themes/) 会从 *卢马*. 的 `top.search` 块 `header-wrapper` 的 `Magento_Search` 不得修改模块。

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

禁用 [!DNL popover] 并恢复标准 [快速搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 功能中，输入以下命令：

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
