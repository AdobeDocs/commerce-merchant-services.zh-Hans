---
title: 安全性和合规性
description: 查看您网站的安全性和合规性要求。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# 安全性和合规性

安全是 [!DNL Payment Services] 和贵机构未传递任何受专用或支付卡行业(PCI)管制的信息 [!DNL Payment Services].

## 商务安全

[!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 包括对多项安全功能的支持。

请参阅 [安全性](https://docs.magento.com/user-guide/stores/security.html)核心用户指南中的{target=&quot;_blank&quot;}，用于查看安全最佳实践，以及了解如何管理管理员会话和凭据、实施CAPTCHA和管理网站限制。

## PCI合规性

支付卡行业(PCI)为接受通过互联网通过信用卡付款的企业制定了一套要求。 除了维护安全的环境外，处理客户信用卡信息的商家还负责满足一些标准准则。

请参阅 [PCI合规指南](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;}以了解详细信息。

商户可以完成 [自我评估调查表](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}，这是一个用于评估持卡人数据安全性的自验证工具。

### 信用卡字段

使用信用卡字段，您的服务中不会传递PCI管制的数据。 您不必存储或维护该数据，这可大大减少PCI合规性问题。

### 卡保险存储

购物者 [金库 — 或“保存” — 其信用卡信息](vaulting.md) 对于您的商店中的未来购买，会与购物者共享最少的信用卡信息（最后四位数、卡的过期日期和卡品牌）。 信用卡信息与支付提供商一起存储。 当卡过期，或者他们不再需要保存的信息时，他们可以删除该令牌，以便支付提供商不再存储该信息。

### PayPal智能按钮

使用PayPal智能按钮，您的服务中不会传递PCI调节的数据。 您不必存储或维护该数据，这可大大减少PCI合规性问题。

出于安全原因，PayPal在结帐期间不传递帐单地址 — 国家/地区、电子邮件和名称是使用的唯一帐单信息。 您可以选择启用网站的PayPal结帐功能，以通过联系PayPal并完成审查流程来返回完整的帐单地址。

PayPal还集成了欺诈保护功能，利用机器学习帮助您打击欺诈。 请参阅PayPal的 [卖家保护文档](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 以了解更多信息。
