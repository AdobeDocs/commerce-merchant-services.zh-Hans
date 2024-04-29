---
title: Commerce服务连接器
description: 了解如何使用生产和沙盒API密钥将Adobe Commerce或Magento Open Source实例集成到服务。
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: e5d9576f0c326dd3a97eeaf9831db0d89b85caff
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

某些Adobe Commerce和Magento Open Source功能由提供支持 [!DNL Commerce Services]  并部署为SaaS（软件即服务）。 要使用这些服务，您必须连接 [!DNL Commerce] 使用生产和沙盒API密钥的实例，并在 [配置](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). 您只需设置一次。

## 可用服务 {#availableservices}

下面列出了 [!DNL Commerce] 您可通过访问的功能 [!DNL Commerce Services Connector]：

| 服务 | 可用性 |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 由Adobe Sensei提供支持 | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) 由Adobe Sensei提供支持 | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce和Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce和Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## 架构

从高层次上说， [!DNL Commerce Services Connector] 由以下核心元素组成：

![Commerce服务连接器架构](assets/saas-config-sync-workflow.png)

以下部分将更详细地讨论其中各个元素。

## 凭据 {#apikey}

生产和沙盒API密钥从生成 [!DNL Commerce] 许可证持有者的帐户，由唯一标识符 [!DNL Commerce] ID (MageID)。 要通过如下服务的授权验证，请执行以下操作 [!DNL Product Recommendations] 或 [!DNL Live Search]，则商户组织的许可证持有人可以生成API密钥集，只要帐户处于良好状态。 这些密钥可在“需要知道”的基础上与系统集成商或代表许可证持有人管理项目和环境的开发团队共享。 此外，解决方案集成商还有权使用 [!DNL Commerce Services]. 如果您是解决方案集成商， [!DNL Commerce] 合作伙伴合同应生成API密钥。

### 生成生产和沙盒API密钥 {#genapikey}

1. 登录 [!DNL Commerce] 帐户位置 [https://account.magento.com](https://account.magento.com/){：target=&quot;_blank&quot;}.

1. 在 **Magento** 选项卡，选择 **API门户** 在侧栏上。

1. 从 _环境_ 菜单，选择 **生产** 或 **沙盒**.

1. 在 _API密钥_ 部分并单击 **新增**.

   这将打开一个用于下载新密钥的对话框。

   ![下载私钥](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > 这是您必须复制或下载密钥的唯一机会。

1. 单击 **下载** 然后单击 **取消**.

1. 对每个环境（生产和沙盒）重复上述步骤。

   此 **API密钥** 部分现在显示您的API（公共）密钥。 在执行以下操作时，您需要生产和沙盒密钥（公共+私有） [选择或创建SaaS项目](#createsaasenv).

## SaaS配置 {#saasenv}

[!DNL Commerce] 必须使用SaaS项目和SaaS数据空间配置实例，以便 [!DNL Commerce Services] 可以将数据发送到正确的位置。 SaaS项目对所有SaaS数据空间进行分组。 SaaS数据空间用于收集和存储以下各项的数据： [!DNL Commerce Services] 去工作。 其中一些数据可从以下导出： [!DNL Commerce] 实例和某些可以从店面的购物者行为中收集。 然后，该数据将保留到安全云存储中。

对象 [!DNL Product Recommendations]，SaaS数据空间包含目录和行为数据。 您可以指向 [!DNL Commerce] 实例到SaaS数据空间，创建者： [选择它](https://docs.magento.com/user-guide/configuration/services/saas.html) 在 [!DNL Commerce] 配置。

>[!WARNING]
>
> 仅在生产环境中使用生产SaaS数据空间 [!DNL Commerce] 安装以避免数据冲突。 否则，您可能会用测试数据污染生产站点数据，从而导致部署延迟。 例如，可能会从暂存数据（如暂存URL）错误地覆盖您的生产产品数据。

### 选择或创建SaaS项目 {#createsaasenv}

要选择或创建SaaS项目，请请求 [!DNL Commerce] 来自的API密钥 [!DNL Commerce] 您商店的许可证持有者。

1. 在 _管理员_ 侧栏，转到 **系统** >服务> **Commerce服务连接器**.

   如果您没有看到 **[!UICONTROL Commerce Services Connector]** 中的部分 [!DNL Commerce] 配置，安装 [!DNL Commerce] 模块满足您的需求 [[!DNL Commerce] 服务](#availableservices). 此外，确保 `magento/module-services-id` 软件包已安装。

1. 在 _沙盒API密钥_ 和 _生产API密钥_ 部分，粘贴您的键值。

   私钥必须包括 `----BEGIN PRIVATE KEY---` 在键的开头和 `----END PRIVATE KEY----` 在私钥的末尾。

1. 单击 **保存**.

任何与键关联的SaaS项目都会显示在 **项目** 中的字段 **SaaS标识符** 部分。

1. 如果不存在任何SaaS项目，请单击 **创建项目**. 然后在 **项目** 字段中，输入SaaS项目的名称。

   创建SaaS项目时， [!DNL Commerce] 根据您的URL生成一个或多个SaaS数据空间 [!DNL Commerce] 许可证：
   - Adobe Commerce — 一个生产数据空间；两个测试数据空间
   - Magento Open Source — 一个生产数据空间；无测试数据空间

1. 选择 **数据空间** 用于的当前配置 [!DNL Commerce] 商店。

>[!WARNING]
>
> 如果您在“我的帐户”的“API门户”部分生成新密钥，请立即更新管理员配置中的API密钥。 如果您在管理员中生成新密钥但未更新它们，则SaaS扩展不再有效，并且您会丢失宝贵的数据。

要更改SaaS项目或数据空间的名称，请单击 **重命名** 旁边都有。 更改名称不会影响您的服务，因为名称只是一个标签，可帮助您识别和区分项目和数据空间。

## IMS组织（可选） {#organizationid}

要将您的Adobe Commerce实例连接到Adobe Experience Platform，请使用Adobe ID登录到您的Adobe帐户。 登录后，与您的Adobe帐户关联的IMS组织将显示在此部分中。

## 目录同步

当 [!DNL Commerce] 实例已成功连接到 [!DNL Commerce Services]，目录同步过程会从您的 [!DNL Commerce] 服务器至 [!DNL Commerce Services]. 目前，只有产品Recommendations使用目录同步服务。 [了解详情](catalog-sync.md) 关于目录同步过程。
