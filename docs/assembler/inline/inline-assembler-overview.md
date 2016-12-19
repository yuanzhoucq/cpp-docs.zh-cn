---
title: "内联汇编程序概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 调用内联汇编程序"
  - "内联汇编程序"
  - "内联程序集, 内联汇编程序"
  - "调用内联汇编程序"
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 内联汇编程序概述
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定**  
  
 可以使用内联汇编程序汇编语言指令嵌入 C 和 c \+ \+ 源代码程序而无需额外的程序集和链接的步骤。  内联汇编中内置了编译器，则不需要单独的程序集 （如 Microsoft 宏汇编程序 \(MASM\)。  
  
 因为内联汇编程序不要求单独的程序集和链接的步骤，则更适合于单独的程序集。  内联程序集代码可以使用任何 C 或 c \+ \+ 变量或函数的名称已在范围内，因此它可以很容易地将它与程序的 C 和 c \+ \+ 代码集成在一起。  并与 C 和 c \+ \+ 的语句，可以混合程序集代码，因为它可以做麻烦或不可能在 C 或 c \+ \+ 单独的任务。  
  
 [\_\_Asm](../../assembler/inline/asm.md) 关键字调用内联汇编，并可以显示 C 或 c \+ \+ 的语句是合法的地方。  它不能单独出现。  它后面必须有程序集指令，指令括在大括号中，或者，最起码，一组一对空括号。  术语" `__asm`块" 这里指的是任何指令或一组说明，不管在大括号中。  
  
 下面的代码是一个简单的`__asm`块括在大括号中。  （代码是一个自定义函数 prolog 序列。  
  
```  
// asm_overview.cpp  
// processor: x86  
void __declspec(naked) main()  
{  
    // Naked functions must provide their own prolog...  
    __asm {  
        push ebp  
        mov ebp, esp  
        sub esp, __LOCAL_SIZE  
    }  
  
    // ... and epilog  
    __asm {  
        pop ebp  
        ret  
    }  
}  
```  
  
 或者，您可以将`__asm`在每个程序集指令前面：  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 由于`__asm`关键字将语句分隔符，也可以将程序集指令放在同一行上：  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE  
```  
  
 **最终 Microsoft 特定**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)