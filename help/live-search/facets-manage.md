---
title: “管理Facet”
description: “了解如何管理现有 [!DNL Live Search] facet”。
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: a17c9ef193394d86f5439f900ebba3dd68d33b45
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# 管理Facet

按照这些说明更新现有Facet的属性或更改其在店面中的显示方式。

## 配置价格方面分组

请参阅 [设置](settings.md) 配置分段价格间隔和分组。

## 编辑Facet

1. 查找要编辑的Facet。
1. 如果列表中有许多方面，请设置 *过滤依据* 更改为以下内容之一：

   * 已固定
   * 动态

   要了解更多信息，请转到 [面类型](facets-type.md).

   ![筛选彩块化](assets/facets-filter-by-cropped.png)

1. 要编辑小平面属性，请单击 **更多** (...)选项。
1. 单击 **编辑**

   ![编辑选项](assets/facet-edit-menu.png)

1. 要编辑Facet标签，请执行以下操作之一：

   * 对于 [!DNL Commerce] 店面，编辑 [属性标签](https://docs.magento.com/user-guide/stores/attributes-product.html).
   * 对于无标题实施，请单击第一列中的值，然后根据需要编辑文本。

   ![编辑标签](assets/facet-edit-label.png)

1. （仅限无头）要更改用于对多面值进行排序的方法，请单击 *排序类型* 列，然后选择以下选项之一：

   * 按字母顺序
   * 计数

   ![编辑计数](assets/facets-edit-count.png)

1. 在 **最大值** 列中，设置要在店面中显示的facet筛选器值的最大数量（从0到10）。
1. 完成后，单击 **保存**.
所做的更改在发布后才会显示在店面中。

## 针/取消针对面

点击时，针脚会更改颜色，用于将面移动到 *固定的Facet* 或 *动态Facet* 中。

1. 将小平面固定到 *过滤器* 列表，在 *动态Facet* 列出并单击灰色的针脚(![固定选择器](assets/btn-pin-gray.png))。
销将变为蓝色，小平面将移动到 *固定的Facet* 中。
1. 要取消固定一个面，请在 *固定的Facet* 列出并单击蓝色针脚(![固定选择器](assets/btn-pin-blue.png))。
销将变灰，小平面将移动到 *动态Facet* 中。

   ![固定和动态Facet](assets/facets-pinned-unpinned.png)

## 移动已固定的面

通过将行移动到其他位置，可以更改已固定小平面的顺序。 已固定的彩块具有 *移动* 图标(![移动选择器](assets/btn-move.png))。 与固定Facet不同，动态Facet无法移动。

1. 在 *固定的Facet* 列表中的
1. 使用 **移动** (![移动选择器](assets/btn-move.png))图标，以将行拖到 *固定的Facet* 中。
更改发布后，重新排序的彩块化会显示在店面中 *过滤器* 列表。

## 删除Facet

1. 在列表中查找该方面，然后单击 **更多** (...)选项。
1. 单击 **删除**.
1. 提示确认时，单击 **删除Facet**.
更改发布后，会从店面中删除该Facet。

## 发布更改

1. 要使用您的更改更新店面，请单击 **发布更改**.
1. 等待大约15分钟，更新才会显示在您的商店中。
