---
title: 内联程序集的调试和列表
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 6e97c2528f480268599f561e8cf4a1df2518c6b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192179"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>内联程序集的调试和列表

**Microsoft 专用**

如果使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项进行编译，则可以使用源级别调试器调试包含内联程序集代码的程序。

在调试器中，您可在 C 或 C++ 和汇编语言行上设置断点。 如果启用混合程序集和源模式，则可同时显示程序集代码的源形式和反汇编形式。

请注意，在一行上放置多个程序集指令或源语言语句可能妨碍调试。 在源模式中，您可使用调试器在单行上设置断点，但不是在同一行的各个语句上。 同样的原则也适用于 **`__asm`** 定义为 C 宏的块，该宏扩展到单个逻辑行。

如果使用[/FAs](../../build/reference/fa-fa-listing-file.md)编译器选项创建混合源和程序集列表，则该列表将包含每个汇编语言行的源和程序集窗体。 宏在列表中将不会扩展，但会在编译时扩展。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
