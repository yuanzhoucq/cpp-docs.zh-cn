---
title: "编译器错误 C2712 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2712"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2712"
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 编译器错误 C2712
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法在要求对象展开的函数中使用 \_\_try  
  
 如果使用[\/EHsc](../../build/reference/eh-exception-handling-model.md)，并且带有结构化异常处理的函数同样需要要求展开（析构）的对象，则会出现错误 C2712。  
  
 可能的解决方案：  
  
-   将要求 SEH 的代码移动到另一个函数中  
  
-   重写使用 SEH 的函数以避免使用具有析构函数的局部变量和参数。  在构造函数或析构函数中不要使用 SEH  
  
-   不使用 \/EHsc 进行编译  
  
 如果调用使用 [\_\_event](../../cpp/event.md) 关键字声明的方法，也可能发生错误 C2712。  因为事件可能在多线程环境中使用，所以编译器将生成阻止基础事件对象操作的代码，然后将生成的代码封装到 SEH [try\-finally 语句](../../cpp/try-finally-statement.md)中。  因此，如果调用事件方法并按值传递其类型具有析构函数的参数，则将发生错误 C2712。  这种情况的一种解决方法是将参数作为常数引用进行传递。  
  
## 示例  
 如果使用 **\/clr:pure** 进行编译并在 `__try` 块中声明指针到函数的静态数组，则会发生 C2712 错误。  静态成员要求编译器在 **\/clr:pure** 下使用动态初始化功能，这意味着 C\+\+ 异常处理。  但是，不允许在 `__try` 块中进行 C\+\+ 异常处理。  
  
 下面的示例生成 C2712，并演示如何修复此错误。  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```