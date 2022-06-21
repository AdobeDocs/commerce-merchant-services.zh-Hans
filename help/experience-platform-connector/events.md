---
title: 事件
description: 了解哪些事件会捕获数据并查看完整的架构定义。
source-git-commit: 0b349ee75fac305e6ba5ea6eb74a76eb8ce1976a
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 项目信标事件

下面列出了 [!DNL Commerce] 事件。 这些事件收集的数据会发送到Adobe Experience Platform Edge。 您还可以创建 [自定义事件](custom-events.md) 来收集开箱即用未提供的其他数据。

单击事件名称可查看完整的架构定义。

| Event | 类型 |
|---|---|
| [添加到购物车](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | 店面 |
| [查看购物车](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | 店面 |
| [查看页面](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | 店面 |
| [查看产品](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | 店面 |
| [开始结帐](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | 店面 |
| 完成结帐 | 店面 |
| [登录](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | 用户档案 |
| [注销](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | 用户档案 |
| [创建帐户](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | 用户档案 |
| [编辑帐户](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | 用户档案 |

>[!NOTE]
>
> 的 `Sign In`, `Sign Out`, `Create Account`和 `Update Account` 事件在尝试特定操作时触发。 它不表示操作成功。
