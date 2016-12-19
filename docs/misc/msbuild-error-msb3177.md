---
title: "MSBuild 错误 MSB3177 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.AllowPartiallyTrustedCallers"
helpviewer_keywords: 
  - "MSB3177"
ms.assetid: 0b2417d5-3bc3-4169-b69c-a4a3cbf47882
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3177
**MSB3177：引用“\<reference\>”不允许部分信任的调用方。**  
  
 当应用程序是部分信任的应用程序时，如果作为项目引用添加的 *引用* 具有强名称，并且没有 APTCA 特性，则会在应用程序清单生成过程中产生此警告。  
  
### 更正此错误  
  
-   将 APTCA 特性添加到引用的程序集，或者停止使用该程序集（如果前一方法不可行）。  
  
## 请参阅  
 [\<PackageFiles\> 元素](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)