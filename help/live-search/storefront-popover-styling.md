---
title: “样式 [!DNL Popover] 元素”
description: “关于自定义 [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: ba3d983372eb60d5cb42e503c3c26c693668a01e
workflow-type: tm+mt
source-wordcount: '202'
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

有关店面元素样式的更多信息，请参阅 [层叠样式表(CSS)](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html) 在 [Frontend开发人员指南](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html).

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

的 [!DNL storefront popover] 可与自定义 [主题](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html) 会从 *卢马*. 的 `top.search` 块 `header-wrapper` 的 `Magento_Search` 不得修改模块。

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

禁用 [!DNL popover] 并恢复标准 [快速搜索](https://docs.magento.com/user-guide/catalog/search-quick.html) 功能中，输入以下命令：

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
