---
title: "MSBuild 错误 MSB3179 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ComImport"
helpviewer_keywords: 
  - "MSB3179"
ms.assetid: fa744f6c-e398-4e60-b4f7-455ace7e3bd2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3179
**MSB3179：隔离 COM 引用“\<assembly\>”时出现问题:“\<error\>”**  
  
 这是一般性错误消息，指示应用程序清单中 RegFree COM 项（由 `IsolatedComReferences` 任务参数指定）的生成问题。  该错误消息的后一部分包含有关问题性质的更多信息。  导致此错误可能的原因是未在生成计算机上正确注册 RegFree COM 组件。  
  
### 更正此错误  
  
-   确保在生成计算机上注册所有的 COM 组件。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)