---
title: Commerce Services Connector
description: 了解如何使用生产和沙盒API密钥将Adobe Commerce或Magento Open Source实例集成到服务中。
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

某些Adobe Commerce和Magento Open Source功能由 [!DNL Commerce Services]  并部署为SaaS（软件即服务）。 要使用这些服务，您必须 [!DNL Commerce] 使用生产和沙盒API密钥的实例，并在 [配置](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). 您只需设置一次。

## 可用服务 {#availableservices}

下面列出了 [!DNL Commerce] 功能 [!DNL Commerce Services Connector]:

| 服务 | 可用性 |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 由Adobe Sensei提供支持 | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) 由Adobe Sensei提供支持 | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce和Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce和Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [Experience Platform连接器](/help/experience-platform-connector/overview.md) | Adobe Commerce |

## 架构

在高层， [!DNL Commerce Services Connector] 由以下核心元素组成：

![Commerce Services连接器架构](assets/saas-config-sync-workflow.png)

以下各节将更详细地讨论这些元素中的每个元素。

## 凭据 {#apikey}

生产和沙盒API密钥是从 [!DNL Commerce] 许可证持有人的帐户，由 [!DNL Commerce] ID(MageID)。 要通过诸如之类的服务的授权验证，请执行以下操作 [!DNL Product Recommendations] 或 [!DNL Live Search]，则商户组织的许可证持有者可以生成API密钥集，只要该帐户完好。 密钥可以与代表许可证持有者管理项目和环境的系统集成商或开发团队“需要知道”共享。 此外，解决方案集成商还有权使用 [!DNL Commerce Services]. 如果您是解决方案集成商，则 [!DNL Commerce] 合作伙伴合同应生成API密钥。

### 生成生产和沙盒API密钥 {#genapikey}

1. 登录到 [!DNL Commerce] 帐户 [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}。

1. 在 **Magento** 选项卡，选择 **API门户** 的问题。

1. 从 _环境_ 菜单，选择 **生产** 或 **沙盒**.

1. 在 _API密钥_ 部分，单击 **新增**.

   此时将打开一个用于下载新密钥的对话框。

   ![下载私钥](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > 这是您必须复制或下载密钥的唯一机会。

1. 单击 **下载** 然后单击 **取消**.

1. 对每个环境（生产和沙盒）重复上述步骤。

   的 **API密钥** 部分现在显示您的API密钥。 当您 [选择或创建SaaS项目](#createsaasenv).

## SaaS配置 {#saasenv}

[!DNL Commerce] 必须使用SaaS项目和SaaS数据空间配置实例，以便 [!DNL Commerce Services] 可以将数据发送到正确的位置。 SaaS项目将所有SaaS数据空间分组。 SaaS数据空间用于收集和存储支持 [!DNL Commerce Services] 工作。 其中某些数据可能会从 [!DNL Commerce] 实例和部分内容可能会从店面上的购物者行为中收集。 然后，该数据将被保留以保护云存储的安全。

对于 [!DNL Product Recommendations]，则SaaS数据空间包含目录和行为数据。 您可以指向 [!DNL Commerce] 实例到SaaS数据空间 [选择](https://docs.magento.com/user-guide/configuration/services/saas.html) 在 [!DNL Commerce] 配置。

>[!WARNING]
>
> 仅在您的生产环境中使用您的生产SaaS数据空间 [!DNL Commerce] 安装以避免数据冲突。 否则，您可能会使用测试数据污染生产站点数据，从而导致部署延迟。 例如，您的生产产品数据可能会被错误地从测试数据（如测试URL）中覆盖。

### 选择或创建SaaS项目 {#createsaasenv}

>[!NOTE]
>
> 如果您没有看到 **[!UICONTROL Commerce Services Connector]** 部分 [!DNL Commerce] 配置中，您必须安装 [!DNL Commerce] 所需模块 [[!DNL Commerce] 服务](#availableservices).

要选择或创建SaaS项目，请请求 [!DNL Commerce] 来自的API密钥 [!DNL Commerce] 您的商店的许可证持有者。

1. 在 _管理员_ 侧栏，转到 **系统** >服务> **Commerce Services Connector**.

1. 在 _沙盒API密钥_ 和 _生产API密钥_ ，请粘贴键值。

   私钥必须包括 `----BEGIN PRIVATE KEY---` 在键和 `----END PRIVATE KEY----` 在私钥的末尾。

1. 单击 **保存**.

任何与您的密钥关联的SaaS项目都会显示在 **项目** 字段 **SaaS标识符** 中。

1. 如果不存在SaaS项目，请单击 **创建项目**. 然后，在 **项目** 字段中，输入SaaS项目的名称。

   创建SaaS项目时， [!DNL Commerce] 会根据您的 [!DNL Commerce] 许可证：
   - Adobe Commerce — 一个生产数据空间；两个测试数据空间
   - Magento Open Source — 一个生产数据空间；没有测试数据空间

1. 选择 **数据空间** 用于 [!DNL Commerce] 存储。

>[!WARNING]
>
> 如果在“我的帐户”的“API门户”部分中生成新密钥，请立即更新“管理员”配置中的API密钥。 如果您在管理员中生成新密钥，并且不更新它们，则您的SaaS扩展将不再有效，并且您会丢失有价值的数据。

要更改SaaS项目或数据空间名称，请单击 **重命名**.

## IMS组织（可选） {#organizationid}

要将Adobe Commerce实例连接到Adobe Experience Platform，请使用Adobe ID登录到您的Adobe帐户。 登录后，与您的Adobe帐户关联的IMS组织将显示在此部分中。

## 目录同步

当 [!DNL Commerce] 实例成功连接到 [!DNL Commerce Services]，则目录同步过程会从 [!DNL Commerce] 服务器到 [!DNL Commerce Services]. [了解更多](catalog-sync.md) 关于目录同步过程。
