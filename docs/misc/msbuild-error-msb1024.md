---
title: "MSBuild 错误 MSB1024 | Microsoft Docs"
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
  - "MSBuild.MultipleSchemasError"
helpviewer_keywords: 
  - "MSB1024"
ms.assetid: dff30870-da1a-479f-998b-03d0f5e16088
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1024
**只能指定一个项目验证架构。**  
  
 只能为 **\/validate** 开关指定一个架构。  
  
### 更正此错误  
  
1.  使用 `/validate:<schema>` 形式，仅指定一个用来验证项目的架构，例如 `/validate:MyExtendedBuildSchema.xsd`  
  
## 请参阅  
 [命令行参考](../Topic/MSBuild%20Command-Line%20Reference.md)