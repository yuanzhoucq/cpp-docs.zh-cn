---
title: "针对 Naked 函数的规则和限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "naked 函数"
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 针对 Naked 函数的规则和限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 以下规则和限制适用于裸函数：  
  
-   不允许使用 `return` 语句。  
  
-   不允许结构化异常处理和 C\+\+ 异常处理构造，因为它们必须在堆栈帧中展开。  
  
-   出于同一原因，禁止任何形式的 `setjmp`。  
  
-   禁止使用 `_alloca` 函数。  
  
-   若要确保局部变量的初始化代码不在 prolog 序列之前出现，函数范围中不允许存在初始化的局部变量。  具体而言，函数范围中不允许有 C\+\+ 对象的声明。  但是，嵌套的范围中可能有初始化的数据。  
  
-   不建议使用帧指针优化（\/Oy 编译器选项），但会自动为裸函数将其取消。  
  
-   不能在函数词法范围中声明 C\+\+ 类对象。  但是，可以在嵌套的块中声明对象。  
  
-   在使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 进行编译时，将忽略 `naked` 关键字。  
  
-   对于 [\_\_fastcall](../cpp/fastcall.md) 裸函数，只要 C\/C\+\+ 代码中存在对某个寄存器参数的引用，prolog 代码就应将该寄存器的值存储到该变量的堆栈位置中。  例如：  
  
```  
// nkdfastcl.cpp  
// compile with: /c  
// processor: x86  
__declspec(naked) int __fastcall  power(int i, int j) {  
   // calculates i^j, assumes that j >= 0  
  
   // prolog  
   __asm {  
      push ebp  
      mov ebp, esp  
      sub esp, __LOCAL_SIZE  
     // store ECX and EDX into stack locations allocated for i and j  
     mov i, ecx  
     mov j, edx  
   }  
  
   {  
      int k = 1;   // return value  
      while (j-- > 0)   
         k *= i;  
      __asm {   
         mov eax, k   
      };  
   }  
  
   // epilog  
   __asm {  
      mov esp, ebp  
      pop ebp  
      ret  
   }  
}  
```  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [Naked 函数调用](../cpp/naked-function-calls.md)