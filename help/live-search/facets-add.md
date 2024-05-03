---
title: "添加Facet"
description: “了解如何添加可过滤的产品属性作为 [!DNL Live Search] 多方面。”
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# 添加Facet

任何可过滤的产品属性都可以用作Facet。 此 *添加Facet* 面板会列出当前彩块化，并可轻松地将其他“产品”属性分配为Facet。 在此三步流程中，选择某个属性作为Facet，根据需要编辑属性，并将更改发布到店面。

![添加Facet](assets/facets-add.png)

## 步骤1：添加方面

1. 在“管理员”中，转到 **营销** > SEO和搜索> **[!DNL Live Search]**.
1. 在 *彩块化* 选项卡，单击 **添加Facet**.
1. 在 *添加Facet* 列表，每个可用属性都有一个单独的 ![“添加”按钮](assets/btn-add.png). 完成以下任一操作：

   * 在 *彩块化属性* 列表，选择要用作Facet的产品属性，然后单击 **添加**.
   * 要查找特定的产品属性，请在 *Search* 盒子。 然后，单击 **添加**.

     要配置价格分段间隔和分组，请参阅 [设置](settings.md). 要了解更多信息，请访问 [Facet类型](facets-type.md).
小平面将添加到 *动态Facet* 列表和 *发布更改* 按钮将变为可用。

1. 如果找不到要添加的Facet，请转到 **商店** >属性> **产品** 并验证该属性是否具有 [必需属性](facets.md) 要用作Facet。 如有必要，请更新属性的以下店面属性：

   * 在搜索中使用 —  `Yes`
   * 在搜索结果分层导航中使用 —  `Yes`
   * 在分层导航中使用 —  `Filterable (with results)`

1. 出现提示时，刷新缓存。

   下次与目录同步时，该Facet将在店面中变得可用 [!DNL Live Search]. 如果Facet在2小时后不可用，请参阅 [同步目录数据](install.md#synchronize-catalog-data).

## 步骤2：编辑Facet属性（可选）

1. 要编辑小平面属性，请单击 **更多** (![更多选择器](assets/btn-more.png))选项。
1. 在菜单上，单击 **编辑**. 然后，根据需要调整以下属性。

   * 标签 — ([Headless](facets-type.md) （仅限）输入要使用的Facet标签。
   * 排序类型 — Facet按字母顺序对所有 [!DNL Commerce] 店面。 对于Headless实施，Facet可以按字母顺序或计数排序。 选项：按字母顺序、计数（仅限Headless）
   * 最大值 — 输入店面中显示的最大Facet值数。 有效条目： 0 - 30；默认值： 8

1. 完成后，单击 **保存**.

   ![编辑Facet](assets/facet-edit.png)

1. 将Facet固定到 *过滤器* 列表，单击灰色图钉(![销钉选择器](assets/btn-pin-gray.png))。
1. 要更改固定多面的顺序，请单击 **移动** (![移动选择器](assets/btn-move.png))图标，并将行拖到中的新位置 *固定的Facet* 部分。

## 步骤3：发布更改

1. Facet完成后，单击 **发布更改**.
1. 等待Facet出现在商店中。
如果Facet在2小时后不可用，请参阅 [验证导出](install.md#synchronize-catalog-data) 安装说明中的。

## 字段描述

| 字段 | 描述 |
|--- |--- |
| 标签 | ([Headless](facets-type.md) 仅限) [Facet标签](facets-type.md) 可编辑店面中可见的内容，以便与您的品牌保持一致。 |
| 排序类型 | 用于 [sort](facets-type.md) 彩块化。 全部 [!DNL Commerce] 店面仅按字母顺序对Facet进行排序。 Headless实施也可以按以下方式排序 `Count`. 选项：<br />按字母顺序 — 按字母顺序对Facet进行排序。<br />计数 — （仅限Headless）根据找到的匹配数对Facet进行排序。 |
| 最大值 | 可在店面中显示的每个Facet的最大值数。 表示一组值的多面均匀分布。 有效条目： 0 - 30；默认值： 8 |

### 控件

| 控件 | 描述 |
|--- |--- |
| ![销钉选择器](assets/btn-pin-blue.png) | 将小平面固定或取消固定到 *过滤器* 列表。 |
| ![更多选择器](assets/btn-more.png) | 显示一个菜单，其中包含可应用于选定小平面的更多操作。 选项：编辑、删除 |
| ![移动选择器](assets/btn-move.png) | 使用 *移动* 图标将固定多面拖到中的其他位置 *固定的Facet* 部分。 |
