---
title: 安全性和合规性
description: 查看您站点的安全性和合规性要求。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 安全性和合规性

安全是以下领域最值得关注的问题 [!DNL Payment Services] 而且您的系统不会传递任何私有或支付卡行业(PCI)管理信息， [!DNL Payment Services].

## 商务安全

[!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 包括对多种安全功能支持。

请参阅 [安全性](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} 查看安全最佳实践，了解如何管理管理员会话和凭据、实施验证码以及管理网站限制。

## PCI合规性

支付卡行业(PCI)为通过互联网接受信用卡付款的企业制定了一系列要求。 除了维护安全的环境外，处理客户信用卡信息的商户还需要满足一些标准准则。

请参阅 [PCI合规性指南](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} 以了解更多信息。

商家可以完成 [自评问卷(SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}，这是一个用于评估持卡人数据安全性的自验证工具。

### 信用卡字段

使用信用卡字段，您的服务中不会传递PCI管制的数据。 您不必存储或维护这些数据，这大大减少了PCI法规遵从性顾虑。

### 3DS

PCI 3-D Secure (3DS)支持在线购买信用卡时购买者与其信用卡发行商进行身份验证。 此额外的安全层有助于防止在线欺诈，并且是欧盟(EU)合规法规要求的一部分。

[!UICONTROL Payment Services] 提供3DS功能，使商家能够遵守欧盟法规，并保护客户和商家免受其商店中的欺诈活动。

如果您是欧盟或英国境内需要3DS合规性的商家，则必须手动启用3DS(它可以 `Off` 默认情况下)，位于 [设置](settings.md#credit-card-fields).

>[!NOTE]
>
>3DS规定适用于业务及持卡人银行位于中国之交易。 [欧洲经济区](https://www.efta.int/eea) (EEA)和英国。 美国商家不需要3DS，但可以根据需要为其交易启用3DS。

商家/店员为买方下单的订单未配置3DS合规措施。

请参阅 [设置中的3DS](settings.md#3ds) 以了解更多信息。

### 卡保险存储

当购物者 [保险库（或“保存”）的信用卡信息](vaulting.md) 对于将来在您的商店中进行的购买，与购物者共享的最少信用卡信息（后四位、卡到期日期和卡品牌）。 信用卡信息存储在支付提供商中。 当卡过期或不再需要保存信息时，可以删除该令牌，以便支付提供商不再存储信息。

请参阅 [信用卡保险存储](vaulting.md) 以了解更多信息。

### PayPal智能按钮

使用PayPal智能按钮，您的服务中不会传递PCI管制的数据。 您不必存储或维护这些数据，这大大减少了PCI法规遵从性顾虑。

为安全起见，PayPal在结账时不会传递账单地址 — 国家/地区、电子邮件和名称是唯一使用的账单信息。 您可以选择启用网站的PayPal签出，以联系PayPal并完成审查流程来返回完整的帐单地址。

PayPal还集成了防欺诈功能，使用机器学习帮助你打击欺诈。 查看PayPal的 [卖方保护文档](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 以了解更多信息。
