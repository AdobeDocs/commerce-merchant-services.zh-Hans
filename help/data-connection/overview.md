---
title: 指南概述
description: 了解如何使用将Adobe Commerce数据与Adobe Experience Platform集成 [!DNL Data Connection] 扩展。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: af54529ad037dc99dbc07cf1a6ac270d17f16870
workflow-type: tm+mt
source-wordcount: '1732'
ht-degree: 0%

---

# [!DNL Data Connection] 介绍

>[!IMPORTANT]
>
>Experience Platform连接器已重命名为 [!DNL Data Connection].

此 [!DNL Data Connection] 扩展可将Adobe Commerce Web实例连接到Adobe Experience Platform和Edge Network。 了解如何 [集成](./mobile-sdk-epc.md) 带有Commerce的Adobe Experience Platform Mobile SDK。

您的Commerce商店包含大量数据。 有关您的购物者如何浏览、查看以及最终购买您网站上的产品的信息可能会揭示创造更个性化购物体验的机会。 虽然这些数据可告知本机商务功能（如购物车价格规则和动态块），但数据仍会孤立在您的商务实例中。

Adobe Experience Platform提供了一套技术，当与您的Commerce商店中的数据结合时，可以将该数据通过Edge Network分发到其他AdobeDX产品，以解锁关于购物者购买行为的洞察。 借助这些深入的见解，您可以跨所有渠道创建更加个性化的购物体验。

下图显示了您的Commerce数据如何从您的商店流向其他AdobeDX产品：

![数据如何流向Experience Platform边缘](assets/commerce-edge.png)

在上图中，您的行为、后台和客户个人资料数据使用SDK、API和源连接器发送到Experience Platform边缘。 您无需完全了解这些部分的工作方式，因为扩展会为您处理数据共享的复杂性。 当事件数据位于边缘时，您可以将该数据提取到其他Experience Platform应用程序中。 例如：

| 应用程序 | 用途 | 用例 |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=zh-Hans) | 用户档案管理和分段服务 | **购买历史记录分段**：商家可以根据特定时段（每月、每季、每年等）识别购买项目的客户。 商家随后可以为这些客户创建区段，并针对这些客户进行促销活动、促销活动以及 _漏斗顶部_ 订阅服务潜在客户的数据。<br> **基于类别的分段**：商家可以查看购买的产品的类别。<br> **基于产品的细分**：商家可以识别始终退货的客户。 现在，提供给他们的优惠和折扣会更加明智。 例如，对于始终返回产品的客户，可以删除免运费。<br> **相似人群拓展定位**：A _相似受众_ 是一种促销活动所用的方法，旨在帮助那些可能会对自己的业务感兴趣的新客户，因为他们与现有客户具有相似的特征。 可以根据行为和事务型数据创建相似区段。<br> **客户倾向**：客户行为的变化可归因于可从事务型数据创建的更深入的客户用户档案。 随着更多数据流入到计算（如产品退货和产品配置）中，倾向分数将有更高的置信度。<br> **交叉销售**：商家可以从Commerce中捕获的精细信息中识别强大的交叉销售和追加销售机会。 |
| [客户 [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | 对整个Commerce历程的深入分析 | **季节性趋势**：商家可以确定季节性趋势，这有助于他们为特定产品的需求定期变化做好准备。 此外，商家可以识别任何产品在不同年份中的整体受欢迎程度变化。<br> **转化分析**：通过了解产品购买时间以及店面展示事件访问权限，商家可以生成丰富的客户配置文件以执行转化分析。 |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | 对客户行为和营销活动绩效的深入分析 | **订单退货**：商家可以识别存在退货模式的客户和较大的客户群体。 这有助于商家改进其商业策略，因为他们了解其客户群行为是什么样的。<br> **订单地址**：根据送货地址，商家可以了解订单是由客户自己下单，还是由其他个人或实体下单。<br> **季节性趋势**：商家可以确定季节性趋势，这有助于他们为特定产品的需求定期变化做好准备。 此外，商家可以识别任何产品在不同年份中的整体受欢迎程度变化。<br> **转化分析**：通过了解产品购买时间以及店面展示事件访问权限，商家可以生成丰富的客户配置文件以执行转化分析。 **注意** Adobe Analytics仅支持行为（店面）事件数据。 Adobe Analytics不支持事务性(backoffice)事件数据。 |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | 跨渠道的活动编排 | **基于行为的历程**：商家可以通过建议客户购买新机型来定位两年前购买手机的客户。 商家可以为这些客户创建个性化的促销活动和促销活动，并使用电子邮件和短信功能进行联系。 此外，商家可以使用历史顺序和行为数据来识别趋势。 例如，如果客户以前购买过具有特定配置的产品，现在又希望再次购买同一产品，则可以通过赋予他们可见性和访问相同产品配置的权限来增强其购买历程。<br> **个性化**：访问客户个人资料信息， [!DNL Journey Optimizer] 可以解锁高度个性化的历程，从而让商家可以通过多个不同渠道联系客户。<br> **已创建新配置文件**：欢迎电子邮件和促销活动可鼓励和影响新客户的购物历程。<br> **已删除配置文件**：商家可以选择停止向已关闭其帐户的客户发送促销电子邮件。 或者，商家也可以建立营销活动以赢回失去的客户。 |

## 将Experience Platform数据提取回Commerce

使用将您的Commerce数据发送到Experience Platform [!DNL Data Connection] 扩展是Commerce数据共享功能的一部分。 另一端（可选扩展）称为 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). 利用此扩展，您可以在Real-Time CDP中构建受众，并将这些受众部署到您的Commerce商店，以告知购物车价格规则、相关产品规则（测试版）和动态块。

从较高层面来看，从Commerce商店到Experience Platform并通过Audience Activation扩展返回的数据流如下所示：

![[!DNL Data Connection] 流量](assets/data-connection.png)

在Commerce与Experience Platform和Experience Platform与Commerce之间设置连接后，数据将继续流动。 您无需重新连接，除非升级时要求重新连接。

## 概念

在这两个系统之间共享数据需要您了解多个概念。

* **数据**  — 与Experience Platform共享的数据是从您店面的浏览器事件、服务器上的后台事件以及配置文件记录数据中收集的数据。 店面活动从购物者在网站上的互动中捕获，并包括如下事件 [`addToCart`](events.md#addtocart)， [`pageView`](events.md#pageview)， [`createAccount`](events.md#createaccount)， [`editAccount`](events.md#editaccount)， [`startCheckout`](events.md#startcheckout)， [`completeCheckout`](events.md#completecheckout)， [`signIn`](events.md#signin)， [`signOut`](events.md#signout)，等等。 请参阅 [店面活动](events.md#storefront-events) 以获取店面活动的完整列表。 服务器端或后台事件，包括 [订单状态](events-backoffice.md#order-status) 信息，例如 [`orderPlaced`](events-backoffice.md#orderplaced)， [`orderReturned`](events-backoffice.md#orderitemreturncompleted)， [`orderShipped`](events-backoffice.md#ordershipmentcompleted)， [`orderCancelled`](events-backoffice.md#ordercancelled)，等等。 请参阅 [后台活动](events-backoffice.md) 以获取后台事件的完整列表。 配置文件记录数据包含创建、更新或删除新配置文件时的信息。 请参阅 [个人资料记录数据](events-profilerecord.md) 了解更多信息。

* **Experience Platform和边缘网络**  — 大多数AdobeDX产品的数据仓库。 发送到Experience Platform的数据然后通过Experience Platform边缘网络传播到AdobeDX产品。 例如，您可以启动Journey Optimizer，从边缘检索特定的Commerce事件数据，并在Journey Optimizer中构建一个弃用的购物车电子邮件。 如果Commerce商店中有任何放弃的购物车，Journey Optimizer随后可以发送该电子邮件。 了解关于 [Experience Platform和边缘网络](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **架构**  — 架构描述的是所发送数据的结构。 在Experience Platform能够摄取Commerce数据之前，您必须构建描述数据结构的架构并对每个字段中可包含的数据类型提供限制。 架构由一个基类以及零个或多个架构字段组组成。 该架构使用XDM结构，所有AdobeDX产品都可以读取该结构。 因此，当您将数据发送至Experience Platform时，可以确保所有DX产品都能理解您的数据。 了解有关 [架构](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **数据集**  — 用于数据收集的存储和管理结构，通常是包含架构（列）和字段（行）的表。 数据集还包含描述其存储的数据的各个方面的元数据。 所有成功引入Adobe Experience Platform的数据都包含在数据集中。 了解有关 [数据集](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **数据流**  — 允许数据从Adobe Experience Platform流向其他AdobeDX产品的ID。 此ID必须关联到您的特定Adobe Commerce实例中的特定网站。 创建此数据流时，请指定您在上面创建的XDM架构。 了解有关 [数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## 支持的架构

此 [!DNL Data Connection] 扩展在以下体系结构上可用：

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## 先决条件

要使用 [!DNL Data Connection] 扩展上，您必须具备以下条件：

* Adobe Commerce 2.4.4或更高版本
* Adobe ID和组织ID
* [Adobe客户端数据层(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html)，这是收集店面事件数据所必需的
* 对其他AdobeDX产品的权利。

## 载入步骤

在高级别上，启用 [!DNL Data Connection] 扩展涉及以下步骤：

1. [安装](install.md) 该 [!DNL Data Connection] 扩展。
1. [登录](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) 到您的Adobe帐户和 [查看以确认](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的组织ID。 组织ID是与您配置的Experience Cloud公司关联的ID。 此ID是由24个字符组成的字母数字字符串，其后跟（且必须包括） `@AdobeOrg`.
1. 确保您拥有 [在Experience Platform中收集数据的权限](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html).
1. 查看 [数据类型](data-ingestion.md) 您可以收集和发送。
1. 创建或更新 [时间序列事件架构](update-xdm.md) 或 [配置文件记录数据架构](profile-data.md) 特定于Commerce的字段组。
1. [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建或更新的架构。 此数据集包含发送到Experience Platform边缘的商务数据。
1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 并选择包含特定于Commerce的字段组的XDM架构。
1. [连接到Commerce Services](../landing/saas.md).
1. [连接到Adobe Experience Platform](connect-data.md).

本指南的其余部分将更详细地介绍所有这些步骤，以便您快速了解并开始使用Commerce商店中AdobeDX产品的强大功能。

>[!NOTE]
>
>对于移动开发人员，了解如何 [集成](./mobile-sdk-epc.md) 带有Commerce的Adobe Experience Platform Mobile SDK。

## 受众

本指南专为希望丰富和个性化其Commerce商店以提升客户购物体验的Adobe Commerce商家而设计。

## 支持

如果您需要本指南中未涉及的信息或问题，请使用以下资源：

* [帮助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 提交票证以接收其他帮助。
