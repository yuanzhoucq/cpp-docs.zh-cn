---
title: "编译器错误 C2884 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2884"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2884"
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2884
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”: 由 using 声明引入，与本地函数“function”冲突  
  
 您尝试多次定义一个函数。  第一个定义是局部定义。  第二个是使用 `using` 声明从命名空间定义的。  
  
 下面的示例生成 C2884：  
  
```  
// C2884.cpp  
namespace A {  
   void z(int);  
}  
  
void f() {  
   void z(int);  
   using A::z;   // C2884 z is already defined  
}  
```