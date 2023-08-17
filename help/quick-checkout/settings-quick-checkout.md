---
title: 配置 [!DNL Quick Checkout] for Adobe Commerce扩展
description: 了解的配置选项 [!DNL Quick Checkout] 以及如何成功载入和设置扩展。
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# [!DNL Quick Checkout] 设置

[!DNL Quick Checkout] for Adobe Commerce and Magento Open Source提供了一个配置视图，其中包含设置扩展所需的所有信息。

要访问这些配置设置，请执行以下操作：

1. 在 _管理员_ 侧栏，转到 **商店** > _设置_ > **配置**.
1. 在左侧面板中，展开 **销售** 并选择 **结帐**.

   ![快速签出](assets/config-new-logo-view.png)

请参阅 [入门](../quick-checkout/onboarding.md) 主题以了解有关如何配置 [!DNL Quick Checkout] 用于Adobe Commerce。

## 启用扩展

![快速签出](assets/enable-method.png)

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Enable] | 网站 | 启用或禁用 [!DNL Quick Checkout] 用于您的网站。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 网站 | 为您的设置方法或环境 [!DNL Quick Checkout]. 选项： [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## 帐户凭据

![快速签出](assets/account-creds.png)

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL API key] | 网站 | 后端用来与交互的私钥 [!DNL Bolt] API。 |
| [!UICONTROL Publishable key] | 网站 | 前端用来与进行交互的密钥 [!DNL Bolt] API。 |
| [!UICONTROL Signing secret] | 网站 | 用于对从收到的请求进行签名验证 [!DNL Bolt]. |

{style="table-layout:auto"}

## 服务设置

![快速签出](assets/service-settings.png)

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Title] | 商店视图 | 在结帐期间在“付款方式”视图中添加文本，以显示此付款选项的标题。 选项： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 网站 | 此 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式的。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | 网站 | 定义Adobe Commerce是否允许与Bolt共享签出跟踪信息。 默认启用。 如果禁用，报表将受影响。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | 网站 | 在客户登录后更改导航流程。 选项： [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | 网站 | 定义 [!DNL Quick Checkout] 允许在签出期间自动登录。 默认启用。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | 网站 | 选择客户自动登录的网络。 默认启用“螺栓”。 选项： [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
