---
title: "在内联程序集中使用和保留寄存器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 注册值"
  - "内联程序集, 寄存器"
  - "保留寄存器"
  - "寄存器, 内联程序集"
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 在内联程序集中使用和保留寄存器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 一般情况下，您不应假定给定的值都登记在`__asm`块开始。  寄存器值并不保证会保留在单独的`__asm`块。  如果您结束的内联代码块，开始另一个，则不能依赖第二块来保留它们的值的第一个块中的寄存器。   `__asm`块继承任何注册值从正常的控制流的结果。  
  
 如果您使用`__fastcall`调用约定时，编译器传递函数参数寄存器，而不是在堆栈上。  这可能会导致问题的函数`__asm`函数具有无法知道哪些参数是哪些寄存器中因阻塞。  如果函数碰巧在 EAX 接收一个参数，并立即将存储 EAX 中的其他部分，则原始参数将会丢失。  此外，必须保留 ECX 寄存器中声明的任何函数 `__fastcall`.  
  
 若要避免此类注册的冲突，请不要使用`__fastcall`约定的函数包含  `__asm`块。  如果指定`__fastcall`约定具有 \/Gr 编译器选项时，全局声明每个函数包含  `__asm`块，  `__cdecl`或  `__stdcall`.  \(  `__cdecl`特性通知编译器为该函数使用 C 调用约定。） 如果您不编译使用 \/Gr，避免声明与函数`__fastcall`特性。  
  
 当使用 `__asm`C\/c \+ \+ 函数中编写程序集语言，您不需要保留 EAX、 EBX、 ECX、 EDX，ESI 或 EDI 收银机。  例如，在电源 2。C 中的示例[编写函数的内联程序集](../../assembler/inline/writing-functions-with-inline-assembly.md)、  `power2`函数不能保留 EAX 寄存器中的值。  但是，使用这些寄存器会影响代码质量由于寄存器分配器不能使用它们来存储值，在`__asm`块。  此外，在内联程序集代码中使用 EBX、 ESI 或 EDI，强制编译器来保存和还原这些寄存器中的函数的序言和跋。  
  
 应保留的作用域 （例如 DS、 SS、 SP、 BP、 和标志寄存器） 使用其他寄存器`__asm`块。  除非您有一些理由更改它们 （如切换堆栈），应保留的 ESP 和 EBP 寄存器。  另请参阅[优化内联程序集](../../assembler/inline/optimizing-inline-assembly.md)。  
  
 某些 SSE 类型需要堆栈 8 字节对齐方式，强制编译器将发出动态堆栈对齐方式的代码。  若要能够进行对齐之后访问局部变量和函数参数，编译器，请保持两个框架指针。  如果编译器执行帧指针省略 \(FPO\)，它将使用 EBP 和 ESP。  如果编译器没有执行 FPO，它将使用 EBX 和 EBP。  为确保代码运行正常，不要修改 EBX asm 代码中如果函数需要动态堆栈对齐方式，因为它无法修改帧指针。  无论是移动 8 个字节对齐的类型，退出该函数，或避免使用 EBX。  
  
> [!NOTE]
>  如果内联程序集代码发生更改时使用的标准或 CLD 说明方向标志，则必须还原为其原始值的标志。  
  
 **最终 Microsoft 特定**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)