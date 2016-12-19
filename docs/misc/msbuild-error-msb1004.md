---
title: "MSBuild 错误 MSB1004 | Microsoft Docs"
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
  - "MSBuild.MissingTargetError"
helpviewer_keywords: 
  - "MSB1004"
ms.assetid: aed36761-ab07-486c-b5eb-48ccb1c387dd
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1004
**指定目标的名称。**  
  
 必须用 **\/target** 开关指定至少一个目标。  
  
### 更正此错误  
  
1.  指定一个或多个目标。  可以使用逗号或分号分隔目标列表，例如 `/target:Clean;Compile`。  或者，可以重复此开关，例如 `/t:Clean /t:` `Compile`  
  
## 请参阅  
 [目标](../Topic/MSBuild%20Targets.md)   
 [命令行参考](../Topic/MSBuild%20Command-Line%20Reference.md)