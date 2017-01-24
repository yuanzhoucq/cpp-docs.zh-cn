---
title: "MSBuild 错误 MSB4142 | Microsoft Docs"
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
  - "MSB4142"
ms.assetid: 56121c76-f952-43d1-ba23-1d1792fef0bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4142
**MSB4142: MSBuildToolsPath 与 ToolsVersion“\<x.x\>”的 MSBuildBinPath 不同。**  
  
 工具集定义为 `MSBuildBinPath` 和 `MSBuildToolsPath` 指定了不同的值。  
  
### 更正此错误  
  
-   确保 `MSBuildBinPath` 和 `MSBuildToolsPath` 的值在工具集定义中相同。  
  
## 请参阅  
 [标准和自定义工具集配置](../Topic/Standard%20and%20Custom%20Toolset%20Configurations.md)   
 [Project 元素 \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他资源](../Topic/Additional%20MSBuild%20Resources.md)