---
title: "MSBuild 错误 MSB4134 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4134"
ms.assetid: 2e4e6beb-c0c9-40ef-b75c-1c16244eba10
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4134
**MSB4134: 将项目加载到引擎中后，将无法设置 DefaultToolsVersion。**  
  
 如果在 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 已经生成项目之后尝试更改 `DefaultToolsVersion` 的值，则会发生此错误。  
  
### 更正此错误  
  
-   在生成项目之前更改 `DefaultToolsVersion` 的值。  
  
## 请参阅  
 <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>   
 <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>   
 [Project 元素 \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他资源](../Topic/Additional%20MSBuild%20Resources.md)