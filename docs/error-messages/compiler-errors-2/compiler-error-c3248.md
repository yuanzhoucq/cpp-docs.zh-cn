---
title: "编译器错误 C3248 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3248"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3248"
ms.assetid: d00b9d7d-b6be-4a5b-bb52-48174ea71fc4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C3248
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function1”: 声明为 "\_\_sealed" 的函数无法被“function2”重写  
  
 派生的类试图重写 [\_\_sealed](../../misc/sealed.md) 虚方法。  
  
 只有使用 **\/clr:oldSyntax** 才可能出现 C3248 错误。  
  
 下面的示例生成 C3248：  
  
```  
// C3248b.cpp // compile with: /clr:oldSyntax using namespace System; __gc struct B { __sealed virtual void func(); }; __gc struct D : B { void func();   // C3248 };  
```