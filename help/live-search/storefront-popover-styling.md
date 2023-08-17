---
title: “样式 [!DNL Popover] 元素”
description: “有关自定义技术说明 [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 样式 [!DNL Popover] 元素

此 [[!DNL storefront popover]](storefront-popover.md) 始终显示产品 `name` 和 `price`，并且无法配置字段选择。 但是， [!DNL popover] 可以使用CSS类为元素设置样式。 例如，以下声明更改了 [!DNL popover] 容器和页脚。

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

以下类选择器可用于设置容器和product元素在 [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

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

## 使用修改的主题 {#working-with-modified-theme}

此 [!DNL storefront popover] 可以与自定义的 [主题](https://developer.adobe.com/commerce/frontend-core/guide/themes/) 所需的文件继承自 *Luma*. 此 `top.search` 中的块 `header-wrapper` 的 `Magento_Search` 不得修改模块。

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
