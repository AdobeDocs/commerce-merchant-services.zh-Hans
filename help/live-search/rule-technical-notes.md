---
title: '"规则技术说明"'
description: “关于使用的技术说明 [!DNL Live Search] 规则。”
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# 规则技术说明

[!DNL Live Search] 规则会根据各种查询条件触发操作，并让商家能够针对各种情况来构建搜索体验。

的当前版本 [!DNL Live Search] 规则基于购物者输入的查询字符串，而不是返回的结果集。 查询字符串可以包含字母数字字符，并且会忽略大小写。 与Facet和同义词一样，规则存储在 `protobuf dynamo`. 在查询时，搜索服务通过 `grpc` 调用 `search-admin-service`.
