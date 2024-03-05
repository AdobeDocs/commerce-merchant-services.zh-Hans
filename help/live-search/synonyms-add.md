---
title: "添加同义词"
description: '"添加 [!DNL Live Search] 同义词，以改善对搜索请求的响应。”'
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: 63318e2eb75bc5fb0a243b6430751b076e541b72
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 添加同义词

通过添加您自己的精选列表来提高客户参与度 [!DNL Live Search] 同义词。 [!DNL Live Search] 最多可以管理200个同义词，每 `Data Space ID`.

![[!DNL Live Search] 同义词](assets/synonym-workspace.png)

## 步骤1：添加同义词

1. 在“管理员”中，转到 **营销** > SEO和搜索> **[!DNL Live Search]**.
1. 对于多个商店，请设置 **范围** 到 [商店视图](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 其中应用了同义词设置。
1. 单击 **同义词** 选项卡。
1. 单击 **添加同义词** 按钮。

## 步骤2：按类型定义同义词

按照 [同义词类型](synonyms-type.md) 您希望创建的。

### 双向同义词

1. 接受默认值 **双向** 选项。

   ![添加双向同义词](assets/synonym-add-two-way.png)


1. 输入 **关键词** 要匹配的术语或短语。
1. 输入 **扩展** 要作为关键字的同义词添加的术语。 用逗号分隔多个术语。
在此示例中，要匹配的关键字是“pants”，而扩展术语集是“trousers， slacks”。

   ![双向同义词示例](assets/synonym-add-two-way-example.png)

1. 完成后，单击 **保存**.
该同义词集显示在列表中，每个术语之间有一个双向箭头，这意味着术语可以互换。

   ![双向同义词](assets/synonym-two-way.png)

### 单向同义词

1. 单击 **单向** 同义词类型。

   ![添加单向同义词](assets/synonym-add-one-way.png)

1. 输入 **关键词** 和 **扩展** 条款。 用逗号分隔多个术语。

   ![单向同义词示例](assets/synonym-add-one-way-example.png)

   在此示例中，关键字是“pants”，而单向扩展术语“capris， peddle-pushers”是“pants”的子集，但具有特定含义。

1. 完成后，单击 **保存**.
同义词集合出现在列表中，有一个从展开项指向关键字的单向箭头，指示这些项是关键字的子集。 每个扩展项之间用加号隔开。

   ![单向同义词](assets/synonym-one-way.png)

## 步骤3：发布更改

1. 同义词完成后，单击 **发布更改**.
1. 等待长达两个小时，您的更新才会在店面中出现。

## 字段描述

| 字段 | 描述 |
|--- |--- |
| [类型](synonyms.md) | 确定同义词与关键字的含义相同，还是关键字的子集。 选项：<br />双向（默认） — 与关键字具有相同含义并返回相同搜索结果的术语<br />单向 — 作为关键字子集的术语。 单向同义词返回的特定产品列表更窄。 |
| 关键词 | 通常与目录中的一系列产品相关的单词。 |
| 扩展 | 与关键字具有相同或相似含义的其他术语。 |
