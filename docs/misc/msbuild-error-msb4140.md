---
title: "MSBuild 错误 MSB4140 | Microsoft Docs"
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
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4140
**MSB4140: 默认 ToolsVersion 既不是在注册表中指定的，也不是在配置文件中指定的。**  
  
 项目没有指定默认的 `ToolsVersion` 值。  因此，[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 不知道要使用哪个值。  
  
### 更正此错误  
  
-   确保在定义工具集的注册表中或在配置文件（如 msbuild.exe.config）中指定了 `DefaultToolsVersion` 值。  
  
## 请参阅  
 [标准和自定义工具集配置](../Topic/Standard%20and%20Custom%20Toolset%20Configurations.md)   
 [Project 元素 \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他资源](../Topic/Additional%20MSBuild%20Resources.md)