---
title: "编译器警告（等级 4）C4343 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4343"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4343"
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 4）C4343
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma optimize\("g",off\) 重写 \/Og 选项  
  
 此警告（仅在 Itanium 处理器系列 \(IPF\) 编译器中有效）报告 pragma [optimize](../../preprocessor/optimize.md) 重写 [\/Og](../../build/reference/og-global-optimizations.md) 编译器选项。  
  
 下面的示例生成 C4343：  
  
```  
// C4343.cpp // compile with: /Og /W4 /LD // processor: IPF #pragma optimize ("g", off)   // C4343  
```