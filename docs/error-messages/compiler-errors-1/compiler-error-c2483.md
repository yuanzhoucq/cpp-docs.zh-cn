---
title: "编译器错误 C2483 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2483"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2483"
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2483
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 带构造函数或析构函数的对象不能声明为“thread”  
  
 用 `thread` 特性声明的变量无法用需要运行时计算的构造函数或其他表达式初始化。  初始化 `thread` 数据时需要静态表达式。  
  
## 示例  
 下面的示例生成 C2483。  
  
```  
// C2483.cpp  
// compile with: /c  
__declspec(thread) struct A {  
   A(){}  
   ~A(){}  
} aa;   // C2483 error  
  
__declspec(thread) struct B {} b;   // OK  
```  
  
## 请参阅  
 [线程](../../cpp/thread.md)