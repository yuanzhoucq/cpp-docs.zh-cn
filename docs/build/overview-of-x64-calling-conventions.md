---
title: "x64 调用约定概述 | Microsoft Docs"
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
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
caps.latest.revision: 12
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# x64 调用约定概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 x86 到 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 的两个重要修改分别是：64 位寻址能力和一组通用展开 64 位寄存器（共 16 个）。  对于这一组展开寄存器，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 只需使用 [\_\_fastcall](../cpp/fastcall.md) 即可调用约定和基于 RISC 的异常处理模型。  `__fastcall` 模型使用寄存器（对前四个变量）和堆栈帧传递其他参数。  
  
 下面的编译器选项有助于您针对 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 优化应用程序：  
  
-   [\/favor（针对体系结构详细信息优化）](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## 调用约定  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 应用程序二进制接口 \(ABI\) 是一种 4 寄存器快速调用调用约定，具有针对这些寄存器的堆栈后备功能。  函数中的参数与这些参数的寄存器之间有一对一的对应关系。  任何大于 8 个字节或不是 1、2、4 或 8 个字节的参数必须由引用传递。  不尝试将单个参数在多个寄存器间传播。  没有使用 x87 寄存器堆栈。  可以使用它，但是必须认为它在函数调用之间是易失性的。  所有浮点操作都是使用 16 个 XMM 寄存器完成的。  参数在寄存器 RCX、RDX、R8 和 R9 中传递。  如果参数是浮点\/双精度型，则它们在 XMM0L、XMM1L、XMM2L 和 XMM3L 中传递。  16 字节的参数由引用传递。  [参数传递](../build/parameter-passing.md) 中详细描述了参数传递。  除这些寄存器外，RAX、R10、R11、XMM4 和 XMM5 也是易失性的。  其他所有寄存器都是非易失性的。  [寄存器使用](../build/register-usage.md) 和 [由调用方或被调用方保存的寄存器](../build/caller-callee-saved-registers.md) 中详细记录了寄存器用法。  
  
 调用方负责为被调用方的参数分配空间，并且必须始终为 4 个寄存器参数分配足够的空间，即使被调用方没有这么多参数。  这有助于简化对 C 非原型函数和 vararg C\/C\+\+ 函数的支持。  对于 vararg 或非原型函数，任何浮点值都必须在相应的常规用途的寄存器中复制。  超过前 4 个的任何参数必须存储在堆栈上，位置在前 4 个的后备存储器之上，在调用之前。  [Varargs](../build/varargs.md) 中提供了 Vararg 函数的详细信息。  [非原型函数](../build/unprototyped-functions.md) 中提供了关于非原型函数的详细信息。  
  
## 对齐方式  
 大多数结构的对齐方式为自然对齐。  主要异常是堆栈指针和 malloc 或 alloca 内存，为了提高性能，它们的对齐方式为 16 字节对齐。  超过 16 字节的对齐必须手动完成，但由于 16 字节是 XMM 操作的常用对齐大小，所以对大多数代码应该足够了。  有关结构布局和对齐方式的更多信息，请参见 [类型和存储](../build/types-and-storage.md)。  有关堆栈布局的信息，请参见 [堆栈使用](../build/stack-usage.md)。  
  
## 展开性  
 必须使用数据 \[称为 xdata 或 ehdata，它指向自 pdata\] 批注所有叶函数 \[这些函数既不调用函数，也不自己分配任何堆栈空间\]，该数据向操作系统描述如何正确展开这些函数以及恢复非易失寄存器。  Prolog 和 epilog 受到严格限制，以便可在 xdata 中正确对它们进行描述。  在不属于 epilog 或 prolog 的任何代码部分中，堆栈指针的对齐方式必须为 16 字节对齐（叶函数除外）。  有关 prolog 和 epilog 函数的正确结构的详细信息，请参见 [保护现场和恢复现场](../build/prolog-and-epilog.md)。  有关异常处理和异常处理\/展开 pdata 和 xdata 的更多信息，请参见 [异常处理 \(x64\)](../build/exception-handling-x64.md)。  
  
## 请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)