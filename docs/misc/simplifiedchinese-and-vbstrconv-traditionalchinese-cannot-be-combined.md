---
title: "不能组合 SimplifiedChinese 和 VbStrConv.TraditionalChinese | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_StrConvSCandTC"
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能组合 SimplifiedChinese 和 VbStrConv.TraditionalChinese
应用程序尝试组合 `VbStrConv` 枚举成员 `SimplifiedChinese` 和 `TraditionalChinese`，而它们是互斥的。  
  
### 更正此错误  
  
-   删除  `VbStrConv.SimplifiedChinese` 或 `VbStrConv.TraditionalChinese`。  
  
## 请参阅  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 枚举](http://msdn.microsoft.com/zh-cn/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [介绍基于 .NET Framework 的国际应用程序](../Topic/Introduction%20to%20International%20Applications%20Based%20on%20the%20.NET%20Framework.md)