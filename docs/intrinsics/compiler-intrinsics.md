---
title: 编译器内部函数
ms.date: 11/04/2016
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 9a014e870d731d7e7d443c3bfefd66884aa50d5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349103"
---
# <a name="compiler-intrinsics"></a>编译器内部函数

大多数函数都包含在库中，但也有一些函数是在编译器中生成的（即内部函数）。 这些被称为内联函数或内部函数。

## <a name="remarks"></a>备注

如果一个函数是内部函数，在通常会采用内联方式插入该函数的代码，从而避免函数调用的开销并可发出该函数的高效率计算机指令。 内部函数通常比等效的内联程序集速度更快，因为优化程序拥有众多内部函数行为方式的内置知识，因此可以优化使用内联程序集无法优化的内容。 此外，优化程序还可以采用不同的方式扩展内部函数、对齐缓冲区或根据上下文和调用自变量进行其他方面的调整。

使用内部函数会影响到代码的可移植性，因为在 Visual C++ 中可用的内部函数如果用其他编译器编译代码则可能不可用，并且对于某些目标体系结构可用的部分内部函数并非对所有体系结构都可用。 但是，内部函数通常比内联程序集可移植性更大。 64 位体系结构要求内部函数，但不支持内联程序集。

某些内部函数（例如 `__assume` 和 `__ReadWriteBarrier`）向编译器提供信息，但这会影响到优化程序的行为。

某些内部函数只能用作内部函数，某些内部函数可以同时用于函数和内部函数实现。 你可以指示编译器使用这两种方式中的一种来使用内部函数实现，具体取决于你是想仅启用特定函数还是想启用所有内部函数。 第一种方法是使用`#pragma intrinsic(`*内部函数的函数名称的列表*`)`。 杂注可用于指定单个内部函数或用逗号分隔的多个内部函数。 第二个是使用[/Oi （生成内部函数）](../build/reference/oi-generate-intrinsic-functions.md)编译器选项，提供给定平台的所有内部函数。 下 **/Oi**，使用`#pragma function(`*内部函数的函数名称的列表*`)`强制使用而不是内部函数的函数调用。 如果特定内部函数的文档说明例程是仅用作内部函数，则无论是否使用内部函数实现 **/Oi**或`#pragma intrinsic`指定。 在所有情况下， **/Oi**或`#pragma intrinsic`允许，但不会强制优化器使用内部函数。 优化程序仍然可以调用函数。

一些标准的 C/C++ 库函数在某些体系结构上可用于内部函数实现。 如果调用 CRT 函数时，使用内部函数实现 **/Oi**命令行上指定。

头文件中， \<intrin.h >，是可用的声明常用内部函数的原型。 制造商指定的内部函数位于\<immintrin.h > 和\<ammintrin.h > 标头文件。 此外，某些 Windows 头文件还可声明在编译器内部函数上映射的函数。

以下部分列出了可用于各种体系结构的所有内部函数。 有关内部函数在特定目标处理器上的工作方式的详细信息，请参阅制造商参考文档。

- [ARM 内部函数](../intrinsics/arm-intrinsics.md)

- [x86 内部函数列表](../intrinsics/x86-intrinsics-list.md)

- [x64 (amd64) 内部函数列表](../intrinsics/x64-amd64-intrinsics-list.md)

- [在所有体系结构上都可用的内部函数](../intrinsics/intrinsics-available-on-all-architectures.md)

- [按字母顺序排序的内部函数列表](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>请参阅

[ARM 汇编程序参考](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft 宏汇编程序参考](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)