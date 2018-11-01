---
title: x64 调用约定概述
ms.date: 11/04/2016
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
ms.openlocfilehash: 37ba3c68310af938f382f88ab4f339166589b96b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444191"
---
# <a name="overview-of-x64-calling-conventions"></a>x64 调用约定概述

X86 和 x64 的两个重要区别是 64 位寻址功能和一组展开为 16 个 64 位寄存器供常规使用。 提供扩展的注册组，使用 x64 [__fastcall](../cpp/fastcall.md)调用约定和一个基于 RISC 的异常处理模型。 `__fastcall`约定使用前四个参数和堆栈帧的寄存器传递其他参数。

以下编译器选项可帮助您优化用于 x64 应用程序：

- [/favor（优化体系结构详细信息）](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="calling-convention"></a>调用约定

默认的 x64 应用程序二进制接口 (ABI) 使用由四个寄存器快速调用调用约定。 被调用方保存这些寄存器的卷影存储作为调用堆栈上分配空间。 函数调用的参数和用于这些参数的寄存器之间没有一对一的对应关系。 任何参数，未满 8 个字节，或者不是 1、 2、 4 或 8 个字节，必须通过引用传递。 不会尝试以跨多个寄存器的单个参数。 X87 寄存器堆栈是未使用。 它可能由被调用方，但必须考虑易失性整个函数调用。 所有的浮动点完成的操作使用 16 个 XMM 寄存器。 整数自变量将传入 RCX、 RDX、 R8 和 R9 寄存器。 浮点数 XMM0L、 XMM1L、 XMM2L 和 XMM3L 中传递参数。 16 字节参数按引用传递。 中详细描述了参数传递[参数传递](../build/parameter-passing.md)。 除了这些寄存器 RAX、 R10、 R11、 XMM4 和 XMM5 被视为易失性。 非易失性的所有其他寄存器。 中详细记录了寄存器用法[注册使用情况](../build/register-usage.md)并[调用方/被调用方保存注册](../build/caller-callee-saved-registers.md)。

调用方负责到被调用方，为参数分配空间，并始终必须分配足够的空间来存储四个注册参数，即使被调用方并不需要这么多参数。 这简化了对非原型 C 语言函数和 vararg C/c + + 函数的支持。 对于 vararg 或 unprototyped 函数，任何浮点值必须在相应的通用寄存器中重复。 任何超出前四个参数都必须存储在前四个，在调用前先的卷影存储上的堆栈。 Vararg 函数详细信息可在[Varargs](../build/varargs.md)。 非原型函数的详细信息中[非原型函数](../build/unprototyped-functions.md)。

## <a name="alignment"></a>对齐方式

大多数结构对齐到其自然对齐。 主要的例外是堆栈指针并`malloc`或`alloca`内存，以便帮助进行性能 16 个字节对齐。 必须手动完成超过 16 字节的对齐方式，但由于 16 个字节是 XMM 操作的常用对齐大小，这也适用于大多数代码。 有关结构布局和对齐方式的详细信息请参阅[类型和存储](../build/types-and-storage.md)。 有关堆栈布局的信息，请参阅[堆栈使用](../build/stack-usage.md)。

## <a name="unwindability"></a>Unwindability

叶函数是不会更改任何非易失寄存器的函数。 非叶函数可能更改非易失性 RSP，例如，通过调用一个函数或为本地变量分配附加的堆栈空间。 要进行恢复非易失寄存器，当处理的异常时，必须使用静态数据，介绍如何正确展开的任意指令处函数批注非叶函数。 此数据将被视为*pdata*，或过程数据，又是指*xdata*、 异常处理数据。 Xdata 包含展开的信息，并可以指向其他 pdata 或异常处理程序函数。 Prolog 和 epilog 是高度受限，以便它们可以成为正确 xdata 中所述。 堆栈指针必须是不可构成了 epilog 或序言中，除叶函数中的代码，任何区域中的 16 个字节对齐。 可以只需通过模拟返回时，因此不需要 pdata 和 xdata 展开叶函数。 有关详细信息的函数 prolog 和 epilog 在正确的结构，请参阅[Prolog 和 Epilog](../build/prolog-and-epilog.md)。 有关异常处理和异常处理和展开 pdata 和 xdata 的详细信息，请参阅[异常处理 (x64)](../build/exception-handling-x64.md)。

## <a name="see-also"></a>请参阅

[x64 软件约定](../build/x64-software-conventions.md)