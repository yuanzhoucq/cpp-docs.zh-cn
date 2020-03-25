---
title: 在内联汇编程序中使用和保留寄存器
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 51147a217ec56c525fc01e1b36a9381b9356ba4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169150"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>在内联汇编程序中使用和保留寄存器

**Microsoft 专用**

通常，`__asm` 块开始时，不应假定寄存器将具有给定值。 不保证将在单独的 `__asm` 块中保留寄存器值。 如果结束一个内联代码块并开始另一个内联代码块，则不能依赖第二个块中的寄存器来保留其在第一个块中的值。 `__asm` 块从正常控制流继承任意寄存器值结果。

如果使用 `__fastcall` 调用约定，则编译器将传递寄存器中而不是堆栈上的函数参数。 这可能会导致带 `__asm` 块的函数出现问题，因为函数无法告知哪一参数位于哪一寄存器中。 如果函数碰巧在 EAX 中收到一个参数并立即在 EAX 中存储其他内容，则原始参数将丢失。 此外，您还必须在使用 `__fastcall` 声明的任何函数中保留 ECX 寄存器。

若要避免此类寄存器冲突，请勿对包含 `__fastcall` 块的函数使用 `__asm` 约定。 如果使用 /Gr 编译器选项全局指定 `__fastcall` 约定，请使用 `__asm` 或 `__cdecl` 来声明每个包含 `__stdcall` 块的函数。 （`__cdecl` 特性告知编译器对该函数使用 C 调用约定。）如果不是用/Gr 进行编译，请避免用 `__fastcall` 属性声明函数。

当使用 `__asm` 在 C/C++ 函数中编写汇编语言时，不需要保留 EAX、EBX、ECX、EDX、ESI 或 EDI 寄存器。 例如，在 POWER2 中。C 示例在[用内联程序集编写函数时](../../assembler/inline/writing-functions-with-inline-assembly.md)，`power2` 函数不会保留 EAX 寄存器中的值。 但是，使用这些寄存器将影响代码质量，因为寄存器分配器无法使用它们在 `__asm` 块中储存值。 此外，通过在内联程序集代码中使用 EBX、ESI 或 EDI，将强制编译器在函数序言和尾声中保存并还原这些寄存器。

您应保留用于 `__asm` 块的范围的其他寄存器（如 DS、SS、SP、BP 和标记寄存器）。 您应保留 ESP 和 EBP 寄存器，除非您出于某种原因要更改它们（例如，切换堆栈）。 另请参阅[优化内联程序集](../../assembler/inline/optimizing-inline-assembly.md)。

某些 SSE 类型需要 8 字节堆栈对齐，以强制编译器发出动态堆栈对齐代码。 为了能在对齐之后访问局部变量和函数参数，编译器将保留两个帧指针。  如果编译器执行帧指针省略（FPO），则它将使用 EBP 和 ESP。  如果编译器不执行 FPO，它将使用 EBX 和 EBP。 为了确保代码正常运行，当函数需要动态堆栈对齐以便能修改帧指针时，请勿在 asm 代码中修改 EBX。 请将 8 字节对齐的类型移出函数，或者避免使用 EBX。

> [!NOTE]
>  如果内联程序集代码使用 STD 或 CLD 指令更改方向标志，你必须将此标志还原为其原始值。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>
