---
title: "MSBuild 错误 MSB3111 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ConfigBindingRedirectsWithPartialTrust"
helpviewer_keywords: 
  - "MSB3111"
ms.assetid: f01286a1-ba27-4733-a431-35ffe9a31356
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3111
**MSB3111: 使用 app.config 绑定重定向要求完全信任。**  
  
 此警告在生成过程检测到应用程序尝试将其中的某些程序集重定向到 app.config 文件内的另一个版本时产生。  对于部分信任的应用程序，app.config 绑定重定向无效。  
  
## 请参阅  
 [产品和包架构引用](../Topic/Product%20and%20Package%20Schema%20Reference.md)