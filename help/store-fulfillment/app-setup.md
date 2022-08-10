---
title: 应用程序设置
description: 设置 [!DNL Store Assist] 要管理端到端商店的在线购买履行工作流程和流程，请按商店订单提货。
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 1fb22b4644d41ea5c60aead3fe2c455dfa3382f8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 应用程序设置

Store Assist是由Walmart Commerce Technologies提供支持的“按实施即服务”(FaaS)平台应用程序。 该应用程序提供商店内实施功能来处理 [!DNL buy online, pick up in store] （桶装）订单。 借助“商店辅助”，商店关联人员可以查看客户订购了哪些项目，更快地挑选正确的项目，并为店内或店内提货客户设置已履行订单。

Store Assist应用程序接收所有订单和客户信息（从订单详细信息到提取时间），并通过移动设备在线提供用于存储关联的数据。 应用程序包括 [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]和 [!UICONTROL Orders] 帮助Store Associates与以下实施活动关联的模块：

- 分配订单交货日期和时间。
- 在客户收到订单提货时，接收他们的通知。
- 为客户切换提交订单。
- 跟踪其分配的存储位置中所有订单的订单状态。

>[!NOTE]
>
>请参阅 [存储协助履行工作流](store-assist-modules.md) 了解有关Store Assist应用程序的更多信息。

## 配置Store Assist应用程序

Store Assist应用程序需要两种类型的配置：

- Adobe Commerce管理系统设置 [管理用户帐户、用户角色、资源权限](user-setup.md)和 [在签入过程中，客户可以选择汽车和模型](check-in-experience-setup.md).

- 用于自定义商店辅助应用程序界面的前端配置设置和其他设置，包括：

   - **为Store Assist应用程序添加品牌** — 使用公司徽标和颜色自定义应用程序用户界面。

   - **更新默认说明** — 自定义“商店辅助挑选”、“暂存”、“切换”和“订单”模块中的说明，以指导Store Associates完成贵公司履行工作流程的每个步骤。

   - **本地化** — 选择应用程序的可用语言。 选择日期和时间格式，然后选择默认度量单位和默认货币。

   - **非活动时间** — 指定应用程序在注销之前必须处于非活动状态的时间。

   - **从商店取消** — 指定是否可以从商店取消订单以及哪些角色具有取消权限

   - **订单清理窗口** — 指定在重新库存之前，挑库单在计划装货时间之前在暂存状态中停留的时间（例如三天）。

   - 自定义应用程序中的所有说明（挑选、暂存、分手）。

   - **领料通知** — 指定客户下订单后是否发送推送通知以启动领料流程。

   - **签入通知** — 指定客户等待时间超过指定时间段后，在订单接收的签入过程中是否发送推送通知 — 签入后。 或者，禁用通知。

   - **切换过程** — 当Store Associate向客户交付订单时启用可选流程，例如，需要客户签名或提示关联人检查客户ID。

   - **在切换时启用项目拒绝** — 允许客户在订单切换期间返回或取消订单项目。
   与沃尔玛商务技术客户服务团队合作，完成商店辅助应用程序的前端配置。

## 应用程序下载和安装

设置并配置Store Assist应用程序后，Store Associates可以从其移动设备下载、安装和登录Store Assist应用程序。

- 验证移动设备是否符合 [硬件和软件要求](solution-requirements.md#store-assist-app-requirements) 的“商店履行”解决方案。

- 从下载Store Assist应用程序 [AppleApp Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target=&quot;_blank&quot;}或 [Google Play商店](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target=&quot;_blank&quot;}。

- Store Associates需要以下信息才能登录：

   - **[!UICONTROL Company name]** 与Store Assist帐户关联

   - **存储协助帐户凭据** — 其帐户的用户名和密码凭据。
   Adobe Commerce管理员可以创建用户帐户并设置 [!DNL Store Assist app] 具有 [店内取货](merchant-store-configuration.md#pickup-location-configuration) 在“管理员存储”设置中启用。
