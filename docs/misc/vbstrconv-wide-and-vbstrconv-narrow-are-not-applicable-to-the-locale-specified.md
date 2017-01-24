---
title: "VbStrConv.Wide 和 VbStrConv.Narrow 不适用于指定的区域设置 | Microsoft Docs"
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
  - "vbrArgument_WideNarrowNotApplicable"
ms.assetid: 5811098c-b124-4caf-8a2b-f81f12f1d5f5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# VbStrConv.Wide 和 VbStrConv.Narrow 不适用于指定的区域设置
应用程序尝试使用 `VbStrConv` 枚举成员 `Wide` 或 `Narrow`，它们不适用于指定的区域设置。  
  
### 更正此错误  
  
1.  删除 `VbStrConv.Wide` 或 `VbStrConv.Narrow`。  
  
## 请参阅  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 枚举](http://msdn.microsoft.com/zh-cn/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [介绍基于 .NET Framework 的国际应用程序](../Topic/Introduction%20to%20International%20Applications%20Based%20on%20the%20.NET%20Framework.md)