---
title: "编译器错误 C3068 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3068"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3068"
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3068
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”:“naked”函数不能包含在发生 C\+\+ 异常时要求展开的对象  
  
 编译器无法在引发异常的 [naked](../../cpp/naked-cpp.md) 函数上执行堆栈展开，因为在该函数中创建了临时对象并且指定了 C\+\+ 异常处理 \([\/EHsc](../../build/reference/eh-exception-handling-model.md)\)。  
  
 若要解决此错误，请采取下列至少一种方法：  
  
-   不使用 \/EHsc 编译。  
  
-   不将函数标记为 `naked`。  
  
-   不在函数中创建临时对象。  
  
 如果函数在堆栈上创建了一个临时对象，并且该函数引发了异常，同时启用了 C\+\+ 异常处理，则当引发异常时，编译器将清理堆栈。  
  
 引发异常时，将为函数执行编译器生成的代码（称为 prolog 和 epilog，它们在 naked 函数中不存在）。  
  
## 示例  
 下面的示例生成 C3068：  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```