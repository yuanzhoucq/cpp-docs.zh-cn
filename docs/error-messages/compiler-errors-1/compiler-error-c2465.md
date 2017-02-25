---
title: "编译器错误 C2465 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2465"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2465"
ms.assetid: 65ba2a9f-d95e-4af3-b60b-1ac59a1e307c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2465
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不能在括号内定义匿名类型  
  
 在带括号的表达式中定义了匿名结构、联合或枚举类型。 这在 C\+\+ 中无效，因为该定义在函数范围中没有意义。