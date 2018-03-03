---
title: "概述 x64 调用约定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac42eb934692fb9eaecf345b75e7544e7078f07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-x64-calling-conventions"></a>x64 调用约定概述
X86 的两个重要区别和[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]是 64 位寻址功能和 16 64 位一平面组寄存器供常规使用。 给定的展开注册集，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]使用[__fastcall](../cpp/fastcall.md)调用约定和基于 RISC 的异常处理模型。 `__fastcall`约定使用寄存器的前四个自变量和堆栈帧将传递其他参数。  
  
 下面的编译器选项可帮助你优化你的应用程序[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]:  
  
-   [/favor（优化体系结构详细信息）](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## <a name="calling-convention"></a>调用约定  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]应用程序二进制接口 (ABI) 默认情况下使用的四个寄存器快速调用调用约定。 作为卷影存储被调用方以保存这些寄存器的情况下，调用堆栈上分配空间。 函数调用的自变量和用于这些自变量的寄存器之间没有严格一对一的对应关系。 必须通过引用传递自变量不适应 8 个字节，或者不是 1、 2、 4 或 8 个字节。 不会尝试以跨多个寄存器的单个自变量。 X87 寄存器堆栈是未使用。 它可能由被调用方，但必须将其视为可变整个函数调用。 所有浮点完成的操作使用 16 个 XMM 寄存器。 整数参数寄存器 RCX、 RDX、 R8 和 R9 中传递。 浮点自变量传递中 XMM0L、 XMM1L、 XMM2L 和 XMM3L。 16 字节自变量通过引用进行传递。 中详细描述参数传递[参数传递](../build/parameter-passing.md)。 除了这些寄存器 RAX、 R10、 R11、 XMM4、 和 XMM5 被视为易失性。 非易失性的所有其他寄存器。 在中详细记录寄存器用法[注册使用情况](../build/register-usage.md)和[调用方/被调用方保存注册](../build/caller-callee-saved-registers.md)。  
  
 调用方负责到被调用方，为参数分配空间，而且必须始终分配足够的空间来存储四个注册参数，，即使被调用方不带这么多参数。 这简化了对非原型 C 语言函数和 vararg C/c + + 函数的支持。 对于 vararg 或非原型函数，任何浮点值必须在相应的通用寄存器中重复。 前四个超出任何参数必须存储在堆栈上，上面第一个四个，在调用前的卷影存储中。 Vararg 函数详细信息可在[Varargs](../build/varargs.md)。 非原型函数的详细信息中[非原型函数](../build/unprototyped-functions.md)。  
  
## <a name="alignment"></a>对齐方式  
 大多数结构对齐到其自然对齐方式。 主要的例外是堆栈指针和`malloc`或`alloca`内存，以便帮助性能 16 个字节对齐。 必须手动完成超过 16 字节的对齐方式，但由于 16 个字节是 XMM 操作的常见对齐大小，这也适用于大多数代码。 有关结构布局和对齐方式的详细信息请参阅[类型和存储](../build/types-and-storage.md)。 有关堆栈布局的信息，请参阅[堆栈使用](../build/stack-usage.md)。  
  
## <a name="unwindability"></a>Unwindability  
 叶函数是不更改任何非易失寄存器的函数。 非叶函数可能更改非易失性 RSP，例如，调用函数，或为局部变量分配附加的堆栈空间。 为了进行恢复非易失寄存器时处理异常时，必须使用介绍如何正确展开任意指令的函数的静态数据添加批注非叶函数。 此数据存储为*pdata*，或过程数据，这反过来指*xdata*、 异常处理数据。 Xdata 包含展开的信息，并可指向其他 pdata 或异常处理程序函数。 起始和 epilog 是高度受限，以便它们可以成为正确 xdata 中所述。 必须为不属于 epilog 或序言中，除叶函数中的代码的任何区域中的 16 字节对齐的堆栈指针。 可以只需通过模拟返回，因此不需要 pdata 和 xdata 位置 leaf 函数。 有关函数起始和 epilog 的适当结构的详细信息，请参阅[Prolog 和 Epilog](../build/prolog-and-epilog.md)。 有关异常处理和异常处理和 pdata 和 xdata 展开的详细信息，请参阅[异常处理 (x64)](../build/exception-handling-x64.md)。  
  
## <a name="see-also"></a>请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)