---
title: “管理Facet”
description: “了解如何管理现有的 [!DNL Live Search] 多方面。”
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: bce69f952e70e2e8dcb892357dea41e18f61e5f6
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# 管理Facet

按照以下说明更新现有Facet的属性或更改其在店面中的表示法。

## 配置价格方面分组

请参阅 [设置](settings.md) 以配置价格分段间隔和分组。

## 编辑Facet

1. 查找要编辑的方面。
1. 如果列表中有许多Facet，请设置 *过滤方式* 更改为以下任一项：

   * 已固定
   * 动态

   要了解更多信息，请访问 [Facet类型](facets-type.md).

   ![筛选Facet](assets/facets-filter-by-cropped.png)

1. 要编辑小平面属性，请单击 **更多** (...)选项。
1. 单击 **编辑**

   ![编辑选项](assets/facet-edit-menu.png)

1. 要编辑多面标签，请执行下列操作之一：

   * 对于 [!DNL Commerce] 店面，编辑 [属性标签](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html).
   * 对于Headless实施，请单击第一列中的值，然后根据需要编辑文本。

   ![编辑标签](assets/facet-edit-label.png)

1. （仅限Headless）要更改用于对Facet值进行排序的方法，请单击 *排序类型* 列并选择以下选项之一：

   * 按字母顺序
   * 计数

   ![编辑计数](assets/facets-edit-count.png)

1. 在 **最大值** 列，设置要在店面中显示的Facet筛选值的最大数量（从0到10）。
1. 完成后，单击 **保存**.
您所做的更改在发布之后才会显示在店面中。

## 固定/取消固定方面

单击此管脚后，其颜色会发生变化，并用于将小平面移动到 *固定的Facet* 或 *动态Facet* 部分。

1. 将Facet固定到 *过滤器* 列表，在 *动态Facet* 列表并单击灰色大头针(![销钉选择器](assets/btn-pin-gray.png))。
销钉变为蓝色，小平面移至 *固定的Facet* 部分。
1. 要取消固定多面，请在以下位置找到该多面： *固定的Facet* 列表并单击蓝色pin (![销钉选择器](assets/btn-pin-blue.png))。
销钉变为灰色，小平面移至 *动态Facet* 部分。

   ![固定和动态Facet](assets/facets-pinned-unpinned.png)

>[!NOTE]
>
>如果存在两个具有相同名称的标签，则固定的Facet排序可能会不一致。

## 移动固定方面

>[!NOTE]
>
>仅在Headless实施中支持固定彩块化的排序。 如果需要排序的Facet，请使用 [!DNL Live Search] PLP小组件。

通过将行移动到不同的位置，可以更改固定小平面的顺序。 固定多面具有 *移动* 图标(![移动选择器](assets/btn-move.png))进行编辑。 与固定多面不同，动态Facet无法移动。

1. 在中查找方面 *固定的Facet* 列表的部分。
1. 使用 **移动** (![移动选择器](assets/btn-move.png))图标，以将行拖到中的新位置 *固定的Facet* 部分。
发布更改后，重新排序的Facet将显示在店面中 *过滤器* 列表。

## 删除facet

1. 在列表中查找方面并单击 **更多** (...)选项。
1. 单击 **删除**.
1. 提示确认时，单击 **删除facet**.
发布更改后，将从店面中删除方面。

## 发布更改

1. 要用更改更新店面，请单击 **发布更改**.
1. 等待大约15分钟，让更新显示在您的存储中。
