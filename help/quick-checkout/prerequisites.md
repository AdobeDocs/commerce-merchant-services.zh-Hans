---
title: '"[!DNL Quick Checkout] 先决条件'
description: “验证您的系统是否满足使用 [!DNL Quick Checkout] 用于Adobe Commerce扩展。”
exl-id: fa61aa73-a2b6-4c69-ab42-cede74c15caa
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# [!DNL Quick Checkout] 先决条件

的 [!DNL Quick Checkout] 与Magento Open Source和Adobe Commerce版本兼容 `>= 2.4.1-p1`.

请参阅 [载入](../quick-checkout/onboarding.md) 主题以了解更多信息。

## 兼容性限制

的 [!DNL Quick Checkout] 存在早期接入计划(EAP)的兼容性问题：

| **问题** | **约束** |
|----------------|-----------------|
| 仅美国 | 此功能仅适用于美国客户 |
| 仅美元 | USD是唯一兼容的货币 |
| [!DNL Amazon Pay] | [!DNL Quick Checkout] 与不兼容 [!DNL Amazon Pay] |
| PWA | 仅支持Luma店面 |
| [!DNL 3D Secure] | [!DNL 3D Secure] 不支持 |
| B2B | 不支持B2B |
| ISPU | [!DNL In-Store Pickup] 不支持(ISPU)功能 |
| 多运送 | 不支持多运送 |

请参阅 [[!DNL Bolt] 限制](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/#limitations) 有关兼容性限制的详细信息主题 [!DNL Bolt] 和 [!DNL Quick Checkout] 扩展。
