---
title: 安全性和合规性
description: 查看您网站的安全性和合规性要求。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: bfce1cb702d634647022a92669d704dd82fe41e6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 安全性和合规性

安全是 [!DNL Payment Services] 和贵机构未传递任何受专用或支付卡行业(PCI)管制的信息 [!DNL Payment Services].

## 商务安全

[!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 包括对多项安全功能的支持。

请参阅 [安全性](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} 在核心用户指南中，查看安全最佳实践，并了解如何管理管理员会话和凭据、实施CAPTCHA以及管理网站限制。

## PCI合规性

支付卡行业(PCI)为接受通过互联网通过信用卡付款的企业制定了一套要求。 除了维护安全的环境外，处理客户信用卡信息的商家还负责满足一些标准准则。

请参阅 [PCI合规指南](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} 以了解更多信息。

商户可以完成 [自我评估调查表](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}，这是一种用于评估持卡人数据安全性的自验证工具。

### 信用卡字段

使用信用卡字段，您的服务中不会传递PCI管制的数据。 您不必存储或维护该数据，这可大大减少PCI合规性问题。

### 3DS

PCI 3-D Secure(3DS)支持购买者在进行在线信用卡购买时使用其信用卡颁发者进行身份验证。 此额外的安全层有助于防止在线欺诈，是欧盟(EU)合规法规的一部分。

[!UICONTROL Payment Services] 提供3DS功能，使商户能够遵守欧盟法规，并保护客户和商户免受其商店中的欺诈活动。

如果您是欧盟或英国境内需要3DS合规的商家，则必须手动打开3DS( `Off` 默认情况下)in [设置](settings.md#credit-card-fields).

>[!NOTE]
>
>3DS要求适用于业务和持卡人银行位于 [欧洲经济区](https://www.efta.int/eea) (EEA)和英国。 美国商户不需要3DS，但可以根据需要为其交易启用3DS。

商家/商店人员为买方下达的订单未配置3DS合规措施。

请参阅 [设置中的3DS](settings.md#3ds) 以了解更多信息。

### 卡保险存储

购物者 [金库 — 或“保存” — 其信用卡信息](vaulting.md) 对于您的商店中的未来购买，会与购物者共享最少的信用卡信息（最后四位数、卡的过期日期和卡品牌）。 信用卡信息与支付提供商一起存储。 当卡过期，或者他们不再需要保存的信息时，他们可以删除该令牌，以便支付提供商不再存储该信息。

请参阅 [信用卡保险](vaulting.md) 以了解更多信息。

### PayPal智能按钮

使用PayPal智能按钮，您的服务中不会传递PCI调节的数据。 您不必存储或维护该数据，这可大大减少PCI合规性问题。

出于安全原因，PayPal在结帐期间不传递帐单地址 — 国家/地区、电子邮件和名称是使用的唯一帐单信息。 您可以选择启用网站的PayPal结帐功能，以通过联系PayPal并完成审查流程来返回完整的帐单地址。

PayPal还集成了欺诈保护功能，利用机器学习帮助您打击欺诈。 请参阅PayPal的 [卖家保护文档](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 以了解更多信息。
