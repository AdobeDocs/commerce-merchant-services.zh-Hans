---
title: “存储协助履行工作流”
description: “了解商店辅助应用程序中提供的Pick、Stage、Hand-Off和Orders模块。 这些模块为BOPIS订单启用了端到端商店履行工作流。 Store Associates使用这些模块来管理和向客户交付商店提货单。”
role: User
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# 存储协助履行工作流

Store Assist应用程序为Store Associates提供四个模块，用于管理在线购买的店内完成过程，按商店订单提货：

- **[挑选](#pick-module)** — 全面了解所有已订购项目和工具，以确保选取正确的项目和正确数量。 商店关联商可以同时选取一个或多个订单以提高效率。

- **[阶段](#stage-module)** — 输入客户前往商店时订单的位置，以便Store Associates可以轻松找到它们以进行订单切换

- **[提交](#hand-off-module)** — 客户到达商店后获取实时通知，以最大程度地缩短等待时间并无缝切换订单

- **[订单数](#orders-module)** — 查看为商店下达的所有订单的列表，以便每个人都知道订单数和每个订单的状态。

>[!NOTE]
>
>在Store Associates使用Store Assist应用程序之前，管理员必须先完成 [应用程序设置过程](app-setup.md).

## 拾取模块

“挑库”模块可帮助存储关联人员查找和扫描客户订购的物品，并将其打包以进行提货。 您可以查看多少订单逾期，并立即开始领取它们。 您还可以选择其他订单以首先进行挑库。 订单按交货到期时间排序，首先是逾期订单。 商店关联人员可以根据操作需要的顺序选择要挑选的订单。

您的联系人也可以选择一次选择一个订单或同时选择多个订单。

领料时，商店关联会看到每个订单的所有要领料的物料列表、数量、价格以及您目录中的产品说明。 此时会显示一个进度栏，帮助他们在领料订单时在“商店辅助”内导航。

在您的关联开始挑库并选择要挑库的物料后，系统会显示所有相关物料信息，例如：大小、颜色、数量、价格、描述、拟合和SKU/UPC。 在领料单时，联营公司有两种活动可用：

- 指示找不到该项目，并触发退款。
- 扫描项目上的条形码。 扫描的目的是验证他们是否选择了正确的项目。 如果相机无法读取条形码，则商店关联商必须手动输入他们选择的项目的SKU。

如果关联者找不到某个项目，他们可以跳过该项目，稍后再返回到该项目。  上述退款仅在他们完成挑库步骤后发出。

## 舞台模块

暂存模块显示在客户到达接收袋装订单之前，该订单的存放位置。 设置此位置是防止订单丢失的关键步骤，当商店关联机构在客户到达之前或您有许多订单时完成其班次。 无论哪种情况，这都有助于您快速找到包含其所有相关信息的正确顺序。

您可以使用自由格式文本栏来指示订单的放置位置：在计数器下、在后室中或在位置B3中 — 所有操作都取决于您的操作。

如果您的关联需要将暂存位置放置到其他位置，则还可以轻松更新应用程序中的暂存位置。

## 切换模块

的 [!UICONTROL Hand Off] 模块显示哪些客户已签入以提取其订单，以及其订单已提货并等待它们的位置。 客人可以在商店内或在外/边的停车场内接到订单。 有关其确切位置的信息，请在签入后显示在此模块中。

在已准备好进行客户切换的订单上进行选择后。 每个人都可以查看订单信息，包括任何未找到的项目、客户等待位置、等待时间、订单存放位置以及客户电话号码（如果可用）。

客户可能已选择替代人员来取订单。 在这种情况下，您会看到应选择订单的人员的姓名和联系信息。

将订单交给客户后，商店关联人必须接受订单或拒绝某些项目。 客户满意后，如果贵公司需要签名，则必须在贵公司的设备上签署订单。

如果客户未签入就到达，则您的关联人可以手动签入。

## 订单模块

“订单”模块显示所有现有订单及其状态。 当客户调用检查其订单时， Store Associates可以通过查找订单号或从“订单”模块中搜索来快速查找信息。