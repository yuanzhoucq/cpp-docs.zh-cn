---
title: "编译器错误 C2495 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2495"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2495"
ms.assetid: bb7066fe-3549-4901-97e4-157f3c04dd57
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2495
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”:“nothrow”只能应用于函数声明或定义  
  
 [nothrow](../../cpp/nothrow-cpp.md) 扩展特性仅可应用到函数声明或定义。  
  
 下面的示例生成 C2495：  
  
```  
// C2495.cpp  
// compile with: /c  
__declspec(nothrow) class X {   // C2495  
   int m_data;  
} x;  
  
__declspec(nothrow) void test();   // OK  
```