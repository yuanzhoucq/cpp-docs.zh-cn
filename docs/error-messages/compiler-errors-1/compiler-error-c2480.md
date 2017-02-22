---
title: "编译器错误 C2480 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2480"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2480"
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2480
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: “thread”仅对静态作用域的数据项有效  
  
 无法与自动变量、非静态数据成员、函数参数一起使用 `thread` 特性，或者在函数声明或定义上使用它。  
  
 仅能对全局变量、静态数据成员和局部静态变量使用 `thread` 特性。  
  
 下面的示例生成 C2480：  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```