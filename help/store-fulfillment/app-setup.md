---
title: 应用程序设置
description: 设置 [!DNL Store Assist] 用于管理在线购买、店内提货的端到端商店履行工作流程和流程的应用程序。
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 应用程序设置

Store Assist是由Walmart Commerce Technologies提供支持的“履行即服务”(FaaS)平台应用程序。 该应用程序提供要处理的店内履行功能 [!DNL buy online, pick up in store] (BOPIS)命令。 借助Store Assist，店员可以查看客户订购的商品、更快地挑选正确的商品以及设置已履行订单以便向客户提供店内或路边取货交货。

Store Assist应用程序会接收所有订单和客户信息（从订单详细信息到取货时间），并通过移动设备在线将相关数据提供给存储合作伙伴。 该应用程序包括 [!UICONTROL Pick]， [!UICONTROL Stage]， [!UICONTROL Handoff]、和 [!UICONTROL Orders] 模块来帮助Store Associates完成以下活动：

- 分配订单交货日期和时间。
- 在客户到达订单提货时收到他们的通知。
- 暂存移交客户的订单。
- 跟踪其分配的商店位置中所有订单的订单状态。

>[!NOTE]
>
>参见 [存储协助完成工作流](store-assist-modules.md) 以详细了解Store Assist应用程序。

## 配置应用商店助手应用程序

Store Assist应用程序需要两种类型的配置：

- Adobe Commerce管理系统设置用于 [管理用户帐户、用户角色、资源权限](user-setup.md)、和 [客户在登记入住过程中可以使用的车辆制造商和型号选择](check-in-experience-setup.md).

- 前端配置设置，用于自定义Store Assist应用程序界面和其他设置，包括：

   - **品牌化Store Assist应用程序** — 使用您公司的徽标和颜色自定义应用程序用户界面。

   - **更新默认说明** — 自定义Store Assist Pick 、 Stage 、 Handoff和Order模块中的说明，以指导Store Associates完成公司工作流的每个步骤。

   - **本地化** — 选择应用程序的可用语言。 选择日期和时间格式，然后选择默认度量单位和默认货币。

   - **非活动时间** — 指定应用程序在注销之前必须处于非活动状态的时间量。

   - **从商店取消** — 指定是否可从存储中取消订单以及哪些角色具有取消权限

   - **订单清理窗口** — 指定超过 [估计的装货提前期](enable-general.md#delivery-method-title-configuration) 挑库订单在重新存储之前仍保留在分段中 — 例如，三天。 默认值为7天。 如果启用此配置，则当此时间到期时，将自动取消订单。 商品重新上架，商家会收到一封取消电子邮件。

   - 自定义所有应用程序内指令（领料、暂存、交货）。

   - **领料通知** — 指定是否在客户下订单后发送推送通知以启动领料流程。

   - **签入通知** — 指定是否在订单提货的登记过程中发送推送通知 — 在登记之后、客户等待时间超过指定时间段之后。 或者，禁用通知。

   - **移交流程** — 在Store Associate向客户交付订单时启用可选流程，例如，需要客户签名或提示关联检查客户ID。

   - **切换时启用项目拒绝** — 允许客户在订单移交期间返回或取消订单项目。
   与Walmart Commerce Technologies Client Services团队合作，完成Store Assist应用程序的前端配置。

## 应用程序下载和安装

设置和配置Store Assist应用程序后，Store Associates可以从其移动设备下载、安装和登录Store Assist应用程序。

- 验证移动设备是否符合 [硬件和软件要求](solution-requirements.md#store-assist-app-requirements) 用于Store Fulfillment解决方案

- 从下载Store Assist应用程序 [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- 存储区关联需要以下信息才能登录：

   - **[!UICONTROL Company name]** 与应用商店助手帐户关联

   - **存储协助帐户凭据** — 其帐户的用户名和密码凭据。
   Adobe Commerce管理员可以创建和管理 [!DNL Store Assist app] 具有下列条件的所有商店位置的用户帐户： [店内取货](merchant-store-configuration.md#pickup-location-configuration) 已在“管理存储”设置中启用。
