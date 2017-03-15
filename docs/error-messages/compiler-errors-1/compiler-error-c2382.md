---
title: "编译器错误 C2382 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2382"
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：重定义；不同的异常规范  
  
 在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下，此错误表示仅对[异常规范](../../cpp/exception-specifications-throw-cpp.md)尝试了函数重载。  
  
 下面的示例生成 C2382：  
  
```  
// C2382.cpp // compile with: /Za /c void f1(void) throw(int) {} void f1(void) throw(char) {}   // C2382 void f2(void) throw(char) {}   // OK  
```